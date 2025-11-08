---
description: 'Instructions for the Serena MCP server, detailing available tools and their usage.'
---

# Serena MCP Server

The Serena MCP server provides advanced tools for understanding and manipulating codebases. It includes capabilities for symbolic code analysis, pattern searching, and code modifications, making it suitable for complex programming tasks.

## Available MCP Tools

The Serena MCP server offers the following tools:

### list_dir

**Tool name**: list_dir
**Full name**: mcp__serena__list_dir

**Description**:
Lists files and directories in the given directory (optionally with recursion). Returns a JSON object with the names of directories and files within the given directory.

**Parameters:**
  * relative_path (required): string - The relative path to the directory to list; pass "." to scan the project root.
  * recursive (required): boolean - Whether to scan subdirectories recursively.
  * skip_ignored_files: boolean - Whether to skip files and directories that are ignored.
  * max_answer_chars: integer - If the output is longer than this number of characters, no content will be returned. -1 means the default value from the config will be used. Don't adjust unless there is really no other way to get the content required for the task.

### find_file

**Tool name**: find_file
**Full name**: mcp__serena__find_file

**Description**:
Finds non-gitignored files matching the given file mask within the given relative path. Returns a JSON object with the list of matching files.

Parameters:
  * file_mask (required): string - The filename or file mask (using the wildcards * or ?) to search for.
  * relative_path (required): string - The relative path to the directory to search in; pass "." to scan the project root.

### search_for_pattern

**Tool name**: search_for_pattern
**Full name**: mcp__serena__search_for_pattern

**Description**:
Offers a flexible search for arbitrary patterns in the codebase, including the possibility to search in non-code files. Generally, symbolic operations like find_symbol or find_referencing_symbols should be preferred if you know which symbols you are looking for.

**Pattern Matching Logic**:
  For each match, the returned result will contain the full lines where the substring pattern is found, as well as optionally some lines before and after it. The pattern will be compiled with DOTALL, meaning that the dot will match all characters including newlines. This also means that it never makes sense to have .* at the beginning or end of the pattern, but it may make sense to have it in the middle for complex patterns. If a pattern matches multiple lines, all those lines will be part of the match. Be careful to not use greedy quantifiers unnecessarily, it is usually better to use non-greedy quantifiers like .*? to avoid matching too much content.

**File Selection Logic**:
  The files in which the search is performed can be restricted very flexibly. Using `restrict_search_to_code_files` is useful if you are only interested in code symbols (i.e., those symbols that can be manipulated with symbolic tools like find_symbol). You can also restrict the search to a specific file or directory, and provide glob patterns to include or exclude certain files on top of that. The globs are matched against relative file paths from the project root (not to the `relative_path` parameter that is used to further restrict the search). Smartly combining the various restrictions allows you to perform very targeted searches. Returns a mapping of file paths to lists of matched consecutive lines.

**Parameters**:
  * substring_pattern (required): string - Regular expression for a substring pattern to search for.
  * context_lines_before: integer - Number of lines of context to include before each match.
  * context_lines_after: integer - Number of lines of context to include after each match.
  * paths_include_glob: string - Optional glob pattern specifying files to include in the search. Matches against relative file paths from the project root (e.g., "*.py", "src/**/*.ts"). Supports standard glob patterns (*, ?, [seq], **, etc.) and brace expansion {a,b,c}. Only matches files, not directories. If left empty, all non-ignored files will be included.
  * paths_exclude_glob: string - Optional glob pattern specifying files to exclude from the search. Matches against relative file paths from the project root (e.g., "*test*", "**/*_generated.py"). Supports standard glob patterns (*, ?, [seq], **, etc.) and brace expansion {a,b,c}. Takes precedence over paths_include_glob. Only matches files, not directories. If left empty, no files are excluded.
  * relative_path: string - Only subpaths of this path (relative to the repo root) will be analyzed. If a path to a single file is passed, only that will be searched. The path must exist, otherwise a `FileNotFoundError` is raised.
  * restrict_search_to_code_files: boolean - Whether to restrict the search to only those files where analyzed code symbols can be found. Otherwise, will search all non-ignored files. Set this to True if your search is only meant to discover code that can be manipulated with symbolic tools. For example, for finding classes or methods from a name pattern. Setting to False is a better choice if you also want to search in non-code files, like in html or yaml files, which is why it is the default.
  * max_answer_chars: integer - If the output is longer than this number of characters, no content will be returned. -1 means the default value from the config will be used. Don't adjust unless there is really no other way to get the content required for the task. Instead, if the output is too long, you should make a stricter query.

### get_symbols_overview

**Tool name**: get_symbols_overview
**Full name**: mcp__serena__get_symbols_overview

**Description**:
Use this tool to get a high-level understanding of the code symbols in a file. This should be the first tool to call when you want to understand a new file, unless you already know what you are looking for. Returns a JSON object containing info about top-level symbols in the file.

**Parameters**:
  * relative_path (required): string - The relative path to the file to get the overview of.
  * max_answer_chars: integer - If the overview is longer than this number of characters, no content will be returned. -1 means the default value from the config will be used. Don't adjust unless there is really no other way to get the content required for the task.

### find_symbol

**Tool name**: find_symbol
**Full name**: mcp__serena__find_symbol

**Description**:
Retrieves information on all symbols/code entities (classes, methods, etc.) based on the given `name_path`, which represents a pattern for the symbol's path within the symbol tree of a single file. The returned symbol location can be used for edits or further queries. Specify `depth > 0` to retrieve children (e.g., methods of a class).

The matching behavior is determined by the structure of `name_path`, which can either be a simple name (e.g. "method") or a name path like "class/method" (relative name path) or "/class/method" (absolute name path). Note that the name path is not a path in the file system but rather a path in the symbol tree **within a single file**. Thus, file or directory names should never be included in the `name_path`. For restricting the search to a single file or directory, the `within_relative_path` parameter should be used instead. The retrieved symbols' `name_path` attribute will always be composed of symbol names, never file or directory names.

**Key aspects of the name path matching behavior**:
  - Trailing slashes in `name_path` play no role and are ignored.
  - The name of the retrieved symbols will match (either exactly or as a substring) the last segment of `name_path`, while other segments will restrict the search to symbols that have a desired sequence of ancestors.
  - If there is no starting or intermediate slash in `name_path`, there is no restriction on the ancestor symbols. For example, passing `method` will match against symbols with name paths like `method`, `class/method`, `class/nested_class/method`, etc.
  - If `name_path` contains a `/` but doesn't start with a `/`, the matching is restricted to symbols with the same ancestors as the last segment of `name_path`. For example, passing `class/method` will match against `class/method` as well as `nested_class/class/method` but not `method`.
  - If `name_path` starts with a `/`, it will be treated as an absolute name path pattern, meaning that the first segment of it must match the first segment of the symbol's name path. For example, passing `/class` will match only against top-level symbols like `class` but not against `nested_class/class`. Passing `/class/method` will match against `class/method` but not `nested_class/class/method` or `method`. Returns a list of symbols (with locations) matching the name.

**Parameters**:
  * name_path (required): string - The name path pattern to search for, see above for details.
  * depth: integer - Depth to retrieve descendants (e.g., 1 for class methods/attributes).
  * relative_path: string - Optional. Restrict search to this file or directory. If None, searches entire codebase. If a directory is passed, the search will be restricted to the files in that directory. If a file is passed, the search will be restricted to that file. If you have some knowledge about the codebase, you should use this parameter, as it will significantly speed up the search as well as reduce the number of results.
  * include_body: boolean - If True, include the symbol's source code. Use judiciously.
  * include_kinds: array - Optional. List of LSP symbol kind integers to include. (e.g., 5 for Class, 12 for Function). Valid kinds: 1=file 2=module, 3=namespace, 4=package, 5=class, 6=method, 7=property, 8=field, 9=constructor, 10=enum, 11=interface, 12=function, 13=variable, 14=constant, 15=string, 16=number, 17=boolean, 18=array, 19=object, 20=key, 21=null, 22=enum member, 23=struct, 24=event, 25=operator, 26=type parameter. If not provided, all kinds are included.
  * exclude_kinds: array - Optional. List of LSP symbol kind integers to exclude. Takes precedence over `include_kinds`. If not provided, no kinds are excluded.
  * substring_matching: boolean - If True, use substring matching for the last segment of `name`.
  * max_answer_chars: integer - Max characters for the JSON result. If exceeded, no content is returned. -1 means the default value from the config will be used.

### find_referencing_symbols

**Tool name**: find_referencing_symbols
**Full name**: mcp__serena__find_referencing_symbols

**Description**:
Finds references to the symbol at the given `name_path`. The result will contain metadata about the referencing symbols as well as a short code snippet around the reference. Returns a list of JSON objects with the symbols referencing the requested symbol.

**Parameters**:
  * name_path (required): string - For finding the symbol to find references for, same logic as in the `find_symbol` tool.
  * relative_path (required): string - The relative path to the file containing the symbol for which to find references. Note that here you can't pass a directory but must pass a file.
  * include_kinds: array - Same as in the `find_symbol` tool.
  * exclude_kinds: array - Same as in the `find_symbol` tool.
  * max_answer_chars: integer - Same as in the `find_symbol` tool.

### replace_symbol_body

**Tool name**: replace_symbol_body
**Full name**: mcp__serena__replace_symbol_body

**Description**:
Replaces the body of the symbol with the given `name_path`.

The tool shall be used to replace symbol bodies that have been previously retrieved (e.g. via `find_symbol`). IMPORTANT: Do not use this tool if you do not know what exactly constitutes the body of the symbol.

**Parameters**:
  * name_path (required): string - For finding the symbol to replace, same logic as in the `find_symbol` tool.
  * relative_path (required): string - The relative path to the file containing the symbol.
  * body (required): string - The new symbol body. The symbol body is the definition of a symbol in the programming language, including e.g. the signature line for functions. IMPORTANT: The body does NOT include any preceding docstrings/comments or imports, in particular.

###  insert_after_symbol

**Tool name**: insert_after_symbol
**Full name**: mcp__serena__insert_after_symbol

**Description**:
Inserts the given body/content after the end of the definition of the given symbol (via the symbol's location). A typical use case is to insert a new class, function, method, field or variable assignment.

**Parameters**:
  * name_path (required): string - Name path of the symbol after which to insert content (definitions in the `find_symbol` tool apply).
  * relative_path (required): string - The relative path to the file containing the symbol.
  * body (required): string - The body/content to be inserted. The inserted code shall begin with the next line after the symbol.

### insert_before_symbol

**Tool name**: insert_before_symbol
**Full name**: mcp__serena__insert_before_symbol

**Description**:
Inserts the given content before the beginning of the definition of the given symbol (via the symbol's location). A typical use case is to insert a new class, function, method, field or variable assignment; or a new import statement before the first symbol in the file.

**Parameters**:
  * name_path (required): string - Name path of the symbol before which to insert content (definitions in the `find_symbol` tool apply).
  * relative_path (required): string - The relative path to the file containing the symbol.
  * body (required): string - The body/content to be inserted before the line in which the referenced symbol is defined.

### rename_symbol

**Tool name**: rename_symbol
**Full name**: mcp__serena__rename_symbol

**Description**:
Renames the symbol with the given `name_path` to `new_name` throughout the entire codebase. Note: for languages with method overloading, like Java, name_path may have to include a method's signature to uniquely identify a method. Returns result summary indicating success or failure.

**Parameters**:
  * name_path (required): string - Name path of the symbol to rename (definitions in the `find_symbol` tool apply).
  * relative_path (required): string - The relative path to the file containing the symbol to rename.
  * new_name (required): string - The new name for the symbol.

### write_memory

**Tool name**: write_memory
**Full name**: mcp__serena__write_memory

**Description**:
Write some information (utf-8-encoded) about this project that can be useful for future tasks to a memory in md format. The memory name should be meaningful.

**Parameters**:
  * memory_file_name (required): string
  * content (required): string
  * max_answer_chars: integer

### read_memory

**Tool name**: read_memory
**Full name**: mcp__serena__read_memory

**Description**:
Read the content of a memory file. This tool should only be used if the information is relevant to the current task. You can infer whether the information is relevant from the memory file name. You should not read the same memory file multiple times in the same conversation.

**Parameters**:
  * memory_file_name (required): string
  * max_answer_chars: integer

### list_memories

**Tool name**: list_memories
**Full name**: mcp__serena__list_memories

**Description**:
List available memories. Any memory can be read using the `read_memory` tool.

### delete_memory

**Tool name**: delete_memory
**Full name**: mcp__serena__delete_memory

**Description**:
Delete a memory file. Should only happen if a user asks for it explicitly, for example by saying that the information retrieved from a memory file is no longer correct or no longer relevant for the project.

**Parameters**:
  * memory_file_name (required): string

### activate_project

**Tool name**: activate_project
**Full name**: mcp__serena__activate_project

**Description**:
Activates the project with the given name or path.

**Parameters**:
  * project (required): string - The name of a registered project to activate or a path to a project directory.

### get_current_config

**Tool name**: get_current_config
**Full name**: mcp__serena__get_current_config

**Description**:
Print the current configuration of the agent, including the active and available projects, tools, contexts, and modes.

### check_onboarding_performed

**Tool name**: check_onboarding_performed
**Full name**: mcp__serena__check_onboarding_performed

**Description**:
Checks whether project onboarding was already performed. You should always call this tool before beginning to actually work on the project/after activating a project, but after calling the initial instructions tool.

### onboarding

**Tool name**: onboarding
**Full name**: mcp__serena__onboarding

**Description**:
Call this tool if onboarding was not performed yet. You will call this tool at most once per conversation. Returns instructions on how to create the onboarding information.

### think_about_collected_information

**Tool name**: think_about_collected_information
**Full name**: mcp__serena__think_about_collected_information

**Description**:
Think about the collected information and whether it is sufficient and relevant. This tool should ALWAYS be called after you have completed a non-trivial sequence of searching steps like find_symbol, find_referencing_symbols, search_files_for_pattern, read_file, etc.

### think_about_task_adherence (serena)

**Tool name**: think_about_task_adherence
**Full name**: mcp__serena__think_about_task_adherence

**Description**:
Think about the task at hand and whether you are still on track. Especially important if the conversation has been going on for a while and there has been a lot of back and forth.

This tool should ALWAYS be called before you insert, replace, or delete code.

### think_about_whether_you_are_done

**Tool name**: think_about_whether_you_are_done
**Full name**: mcp__serena__think_about_whether_you_are_done

**Description**:
Whenever you feel that you are done with what the user has asked for, it is important to call this tool.

### initial_instructions

**Tool name**: initial_instructions
**Full name**: mcp__serena__initial_instructions

**Description**:
Provides the 'Serena Instructions Manual', which contains essential information on how to use the Serena toolbox. Call this tool if you have not yet read this very important manual!
