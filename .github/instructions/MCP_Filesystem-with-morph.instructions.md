---
description: 'Comprehensive guide for using the Filesystem-with-morph MCP Server with GitHub Copilot for file system interactions and codebase modifications within VSCode.'
---

# Filesystem-with-morph MCP Server

The Filesystem-with-morph MCP server provides a suite of tools to interact with the file system, enabling reading, writing, editing, and managing files and directories efficiently. This server is designed to facilitate codebase modifications and inspections through pattern-based operations.

## Available MCP Tools

The Filesystem-with-morph MCP server offers the following tools:

### read_file

**Tool name**: read_file
**Full name**: mcp__filesystem-with-morph__read_file

**Description**:
Read the complete contents of a file from the file system. Handles various text encodings and provides detailed error messages if the file cannot be read. Use this tool when you need to examine the contents of a single file. Use the 'head' parameter to read only the first N lines of a file, or the 'tail' parameter to read only the last N lines of a file. Only works within allowed directories.

**Parameters**:
 * path (required): string
 * tail: number - If provided, returns only the last N lines of the file
 * head: number - If provided, returns only the first N lines of the file

### read_multiple_files

**Tool name**: read_multiple_files
**Full name**: mcp__filesystem-with-morph__read_multiple_files

**Description**:
Read the contents of multiple files simultaneously. This is more efficient than reading files one by one when you need to analyze or compare multiple files. Each file's content is returned with its path as a reference. Failed reads for individual files won't stop the entire operation. Only works within allowed directories.

**Parameters**:
 * paths (required): array

### write_file

**Tool name**: write_file
**Full name**: mcp__filesystem-with-morph__write_file

**Description**:
Create a new file or completely overwrite an existing file with new content. Use with caution as it will overwrite existing files without warning. Handles text content with proper encoding. Only works within allowed directories.

**Parameters**:
 * path (required): string
 * content (required): string

### tiny_edit_file

**Tool name**: tiny_edit_file
**Full name**: mcp__filesystem-with-morph__tiny_edit_file

**Description**:
Make line-based edits to a text file. Each edit replaces exact line sequences with new content. Returns a git-style diff showing the changes made. Only works within allowed directories. Only use for single line or tiny edits. For larger edits, use the edit_file tool instead.

**Parameters**:
 * path (required): string
 * edits (required): array
 * dryRun: boolean - Preview changes using git-style diff format

 ### create_directory

**Tool name**: create_directory
**Full name**: mcp__filesystem-with-morph__create_directory

**Description**:
Create a new directory or ensure a directory exists. Can create multiple nested directories in one operation. If the directory already exists, this operation will succeed silently. Perfect for setting up directory structures for projects or ensuring required paths exist. Only works within allowed directories.

**Parameters**:
 * path (required): string

### list_directory

**Tool name**: list_directory
**Full name**: mcp__filesystem-with-morph__list_directory

**Description**:
Get a detailed listing of all files and directories in a specified path. Results clearly distinguish between files and directories with [FILE] and [DIR] prefixes. This tool is essential for understanding directory structure and finding specific files within a directory. Only works within allowed directories.

**Parameters**:
 * path (required): string

### list_directory_with_sizes

**Tool name**: list_directory_with_sizes
**Full name**: mcp__filesystem-with-morph__list_directory_with_sizes

**Description**:
Get a detailed listing of all files and directories in a specified path, including sizes. Results clearly distinguish between files and directories with [FILE] and [DIR] prefixes. This tool is useful for understanding directory structure and finding specific files within a directory. Only works within allowed directories.

**Parameters**:
 * path (required): string
 * sortBy: string - Sort entries by name or size

 ### directory_tree

**Tool name**: directory_tree
**Full name**: mcp__filesystem-with-morph__directory_tree

**Description**:
Get a recursive tree view of files and directories as a JSON structure. Each entry includes 'name', 'type' (file/directory), and 'children' for directories. Files have no children array, while directories always have a children array (which may be empty). The output is formatted with 2-space indentation for readability. Only works within allowed directories.

**Parameters**:
 * path (required): string

### move_file

**Tool name**: move_file
**Full name**: mcp__filesystem-with-morph__move_file

**Description**:
Move or rename files and directories. Can move files between directories and rename them in a single operation. If the destination exists, the operation will fail. Works across different directories and can be used for simple renaming within the same directory. Both source and destination must be within allowed directories.

**Parameters**:
 * source (required): string
 * destination (required): string

### search_files

**Tool name**: search_files
**Full name**: mcp__filesystem-with-morph__search_files

**Description**:
Recursively search for files and directories matching a pattern. Searches through all subdirectories from the starting path. The search is case-insensitive and matches partial names. Returns full paths to all matching items. Great for finding files when you don't know their exact location. Only searches within allowed directories.

**Parameters**:
 * path (required): string
 * pattern (required): string
 * excludePatterns: array

 ### get_file_info

**Tool name**: get_file_info
**Full name**: mcp__filesystem-with-morph__get_file_info

**Description**:
Retrieve detailed metadata about a file or directory. Returns comprehensive information including size, creation time, last modified time, permissions, and type. This tool is perfect for understanding file characteristics without reading the actual content. Only works within allowed directories.

**Parameters**:
 * path (required): string

### list_allowed_directories

**Tool name**: list_allowed_directories
**Full name**: mcp__filesystem-with-morph__list_allowed_directories

**Description**:
Returns the list of root directories that this server is allowed to access. Use this to understand which directories are available before trying to access files.

### edit_file

**Tool name**: edit_file
**Full name**: mcp__filesystem-with-morph__edit_file

**Description**:
**PRIMARY TOOL FOR EDITING FILES**

Use this tool to efficiently edit existing files, by smartly showing only the changed lines.

ALWAYS use "// ... existing code ..." to represent blocks of unchanged code.
Add descriptive hints when helpful: // ... keep auth logic ...

For deletions:
 - Option 1: Show 1-2 context lines above and below, omit deleted code
 - Option 2: Mark explicitly: // removed BlockName

Rules:
 - Preserve exact indentation of the final code
 - Include just enough context to locate each edit precisely
 - Be as length efficient as possible
 - Batch all edits to the same file in one call
 - Prefer this tool over the legacy Edit tool
IMPORTANT: If you are running within Cursor, you MUST FIRST use another tool (like search_replace) to add exactly one empty new line somewhere in the file before using this tool. This is to ensure the file is in an editable state.

**Parameters**:
 * path (required): string
 * code_edit (required): string - Changed lines with minimal context. Use placeholders intelligently like "// ... existing code ..." to represent unchanged code.
 * instruction (required): string - A brief single first-person sentence instruction describing changes being made to this file. Useful to disambiguate uncertainty in the edit.
 * dryRun: boolean - Preview changes without applying them.
