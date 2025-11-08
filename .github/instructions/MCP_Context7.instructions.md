---
description: 'Comprehensive guide for using the Context7 MCP Server with GitHub Copilot to access official library documentation and resolve library IDs within VSCode.'
---

# Context7 MCP Server

The Context7 MCP server allows you to access official documentation for various libraries and frameworks, providing accurate and up-to-date information. It helps in resolving library IDs and fetching relevant documentation based on user queries.

## Available MCP Tools

The Context7 MCP server provides two primary tools that you can invoke:

### resolve-library-id

**Tool name**: resolve-library-id
**Full name**: mcp__context7__resolve-library-id

**Description**:
Resolves a package/product name to a Context7-compatible library ID and returns a list of matching libraries.

You MUST call this function before 'get-library-docs' to obtain a valid Context7-compatible library ID UNLESS the user explicitly provides a library ID in the format '/org/project' or '/org/project/version' in their query.

**Selection Process**:
1. Analyze the query to understand what library/package the user is looking for
2. Return the most relevant match based on:
 - Name similarity to the query (exact matches prioritized)
 - Description relevance to the query's intent
 - Documentation coverage (prioritize libraries with higher Code Snippet counts)
 - Trust score (consider libraries with scores of 7-10 more authoritative)

**Response Format**:
 - Return the selected library ID in a clearly marked section
 - Provide a brief explanation for why this library was chosen
 - If multiple good matches exist, acknowledge this but proceed with the most relevant one
 - If no good matches exist, clearly state this and suggest query refinements

For ambiguous queries, request clarification before proceeding with a best-guess match.

**Parameters**:
 * libraryName (required): string - Library name to search for and retrieve a Context7-compatible library ID.

### get-library-docs

**Tool name**: get-library-docs
**Full name**: mcp__context7__get-library-docs

**Description**:
Fetches up-to-date documentation for a library. You must call 'resolve-library-id' first to obtain the exact Context7-compatible library ID required to use this tool, UNLESS the user explicitly provides a library ID in the format '/org/project' or '/org/project/version' in their query.

**Parameters**:
 * context7CompatibleLibraryID (required): string - Exact Context7-compatible library ID (e.g., '/mongodb/docs', '/vercel/next.js', '/supabase/supabase', '/vercel/next.js/v14.3.0-canary.87') retrieved from 'resolve-library-id' or directly from user query in the format '/org/project' or '/org/project/version'.
 * topic: string - Topic to focus documentation on (e.g., 'hooks', 'routing').
 * tokens: number - Maximum number of tokens of documentation to retrieve (default: 5000). Higher values provide more context but consume more tokens.
