---
description: 'Comprehensive guide for using the Tavily MCP Server with GitHub Copilot for efficient web search, content extraction, and site mapping within VSCode.'
---

# Tavily MCP Server

The Tavily MCP server provides a suite of tools to interact with the Tavily platform, enabling efficient management of user queries and responses. This server is designed to facilitate seamless integration with the Tavily ecosystem.

## Available MCP Tools

The Tavily MCP server offers the following tools:

### tavily-search

**Tooln name**: tavily-search
**Full name**: mcp__tavily-mcp__tavily-search

**Description**: A powerful web search tool that provides comprehensive, real-time results using Tavily's AI search engine. Returns relevant web content with customizable parameters for result count, content type, and domain filtering. Ideal for gathering current information, news, and detailed web content analysis.

**Parameters**:
 * query (required): string - Search query
 * search_depth: string - The depth of the search. It can be 'basic' or 'advanced'
 * topic: string - The category of the search. This will determine which of our agents will be used for the search
 * days: number - The number of days back from the current date to include in the search results. This specifies the time frame of data to be retrieved. Please note that this feature is only available when using the 'news' search topic
 * time_range: string - The time range back from the current date to include in the search results. This feature is available for both 'general' and 'news' search topics
 * start_date: string - Will return all results after the specified start date. Required to be written in the format YYYY-MM-DD.
 * end_date: string - Will return all results before the specified end date. Required to be written in the format YYYY-MM-DD
 * max_results: number - The maximum number of search results to return
 * include_images: boolean - Include a list of query-related images in the response
 * include_image_descriptions: boolean - Include a list of query-related images and their descriptions in the response
 * include_raw_content: boolean - Include the cleaned and parsed HTML content of each search result
 * include_domains: array - A list of domains to specifically include in the search results, if the user asks to search on specific sites set this to the domain of the site
 * exclude_domains: array - List of domains to specifically exclude, if the user asks to exclude a domain set this to the domain of the site
 * country: string - Boost search results from a specific country. This will prioritize content from the selected country in the search results. Available only if topic is general. Country names MUST be written in lowercase, plain English, with spaces and no underscores.
 * include_favicon: boolean - Whether to include the favicon URL for each result

### tavily-extract

**Tool name**: tavily-extract
**Full name**: mcp__tavily-mcp__tavily-extract

**Description**: A powerful web content extraction tool that retrieves and processes raw content from specified URLs, ideal for data collection, content analysis, and research tasks.

**Parameters**:
 * urls (required): array - List of URLs to extract content from
 * extract_depth: string - Depth of extraction - 'basic' or 'advanced', if usrls are linkedin use 'advanced' or if explicitly told to use advanced
 * include_images: boolean - Include a list of images extracted from the urls in the response
 * format: string - The format of the extracted web page content. markdown returns content in markdown format. text returns plain text and may increase latency.
 * include_favicon: boolean - Whether to include the favicon URL for each result

### tavily-crawl

**Tool name**: tavily-crawl
**Full name**: mcp__tavily-mcp__tavily-crawl

**Description**: A powerful web crawler that initiates a structured web crawl starting from a specified base URL. The crawler expands from that point like a graph, following internal links across pages. You can control how deep and wide it goes, and guide it to focus on specific sections of the site.

**Parameters**:
 * url (required): string - The root URL to begin the crawl
 * max_depth: integer - Max depth of the crawl. Defines how far from the base URL the crawler can explore.
 * max_breadth: integer - Max number of links to follow per level of the tree (i.e., per page)
 * limit: integer - Total number of links the crawler will process before stopping
 * instructions: string - Natural language instructions for the crawler. Instructions specify which types of pages the crawler should return.
 * select_paths: array - Regex patterns to select only URLs with specific path patterns (e.g., /docs/.*, /api/v1.*)
 * select_domains: array - Regex patterns to restrict crawling to specific domains or subdomains (e.g., ^docs\.example\.com$)
 * allow_external: boolean - Whether to return external links in the final response
 * extract_depth: string - Advanced extraction retrieves more data, including tables and embedded content, with higher success but may increase latency
 * format: string - The format of the extracted web page content. markdown returns content in markdown format. text returns plain text and may increase latency.
 * include_favicon: boolean - Whether to include the favicon URL for each result

### tavily-map

**Tool name**: tavily-map
**Full name**: mcp__tavily-mcp__tavily-map

**Description**:
A powerful web mapping tool that creates a structured map of website URLs, allowing you to discover and analyze site structure, content organization, and navigation paths. Perfect for site audits, content discovery, and understanding website architecture.

**Parameters**:
 * url (required): string - The root URL to begin the mapping
 * max_depth: integer - Max depth of the mapping. Defines how far from the base URL the crawler can explore
 * max_breadth: integer - Max number of links to follow per level of the tree (i.e., per page)
 * limit: integer - Total number of links the crawler will process before stopping
 * instructions: string - Natural language instructions for the crawler
 * select_paths: array - Regex patterns to select only URLs with specific path patterns (e.g., /docs/.*, /api/v1.*)
 * select_domains: array - Regex patterns to restrict crawling to specific domains or subdomains (e.g., ^docs\.example\.com$)
 * allow_external: boolean - Whether to return external links in the final response
