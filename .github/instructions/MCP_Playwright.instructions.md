---
description: 'Comprehensive guide for using the Playwright MCP Server with GitHub Copilot for browser automation, testing, and web interaction within VSCode.'
---

# Playwright MCP Server

The Playwright MCP Server allows GitHub Copilot to control a web browser using the Playwright library. This enables advanced browser automation, testing, and web interaction capabilities directly from VSCode.

## Available MCP Tools

The Playwright MCP Server offers the following tools:

### Close browser

**Tool Name:**: browser_close
**Full name:**: mcp__playwright__browser_close

**Description:**:
Close the page

### Resize browser window

**Tool Name:**: browser_resize
**Full name:**: mcp__playwright__browser_resize

**Description:**:
Resize the browser window

**Parameters:**
  * width (required): number - Width of the browser window
  * height (required): number - Height of the browser window

### Get console messages

**Tool Name:**: browser_console_messages
**Full name:**: mcp__playwright__browser_console_messages

**Description:**:
Returns all console messages

**Parameters:**
  * onlyErrors: boolean - Only return error messages

### Handle a dialog

**Tool Name:**: browser_handle_dialog
**Full name:**: mcp__playwright__browser_handle_dialog

**Description:**:
Handle a dialog

**Parameters:**
  * accept (required): boolean - Whether to accept the dialog.
  * promptText: string - The text of the prompt in case of a prompt dialog.

### Evaluate JavaScript

**Tool Name:**: browser_evaluate
**Full name:**: mcp__playwright__browser_evaluate

**Description:**:
Evaluate JavaScript expression on page or element

**Parameters:**
  * function (required): string - () => { /* code */ } or (element) => { /* code */ } when element is provided
  * element: string - Human-readable element description used to obtain permission to interact with the element
  * ref: string - Exact target element reference from the page snapshot

### Upload files

**Tool name:**: browser_file_upload
**Full name:**: mcp__playwright__browser_file_upload

**Description:**:
Upload one or multiple files

**Parameters:**
  * paths: array - The absolute paths to the files to upload. Can be single file or multiple files. If omitted, file chooser is cancelled.

### Fill form

**Tool name:**: browser_fill_form
**Full name:**: mcp__playwright__browser_fill_form

**Description:**:
Fill multiple form fields

**Parameters:**
  * fields (required): array - Fields to fill in

### Install the browser specified in the config

**Tool name:**: browser_install
**Full name:**: mcp__playwright__browser_install

**Description:**:
Install the browser specified in the config. Call this if you get an error about the browser not being installed.

### Press a key

**Tool name:**: browser_press_key
**Full name:**: mcp__playwright__browser_press_key

**Description:**:
Press a key on the keyboard

**Parameters:**
  * key (required): string - Name of the key to press or a character to generate, such as `ArrowLeft` or `a`

### Type text

**Tool name:**: browser_type
**Full name:**: mcp__playwright__browser_type

**Description:**:
Type text into editable element

**Parameters:**
  * element (required): string - Human-readable element description used to obtain permission to interact with the element
  * ref (required): string - Exact target element reference from the page snapshot
  * text (required): string - Text to type into the element
  * submit: boolean - Whether to submit entered text (press Enter after)
  * slowly: boolean - Whether to type one character at a time. Useful for triggering key handlers in the page. By default entire text is filled in at once.

### Navigate to a URL

**Tool name:**: browser_navigate
**Full name:**: mcp__playwright__browser_navigate

**Description:**:
Navigate to a URL

**Parameters:**
  * url (required): string - The URL to navigate to

### Go back

**Tool name:**: browser_navigate_back
**Full name:**: mcp__playwright__browser_navigate_back

**Description:**:
Go back to the previous page

### List network requests

**Tool name:**: browser_network_requests
**Full name:**: mcp__playwright__browser_network_requests

**Description:**:
Returns all network requests since loading the page

### Take a screenshot

**Tool name:**: browser_take_screenshot
**Full name:**: mcp__playwright__browser_take_screenshot

**Description:**:
Take a screenshot of the current page. You can't perform actions based on the screenshot, use browser_snapshot for actions.

**Parameters:**
  * element: string - Human-readable element description used to obtain permission to snapshot the element. If not provided, the snapshot will be taken of the entire page.
  * ref: string - Exact target element reference from the page snapshot. If not provided, the snapshot will be taken of the entire page.
  * fullPage: boolean - When true, takes a snapshot of the full scrollable page, instead of the currently visible viewport. Cannot be used with element snapshots.

### Page snapshot

**Tool name:**: browser_snapshot
**Full name:**: mcp__playwright__browser_snapshot

**Description:**:
Capture accessibility snapshot of the current page, this is better than screenshot

### Click

**Tool name:**: browser_click
**Full name:**: mcp__playwright__browser_click

**Description:**:
Perform click on a web page

**Parameters:**
  * element (required): string - Human-readable element description used to obtain permission to interact with the element
  * ref (required): string - Exact target element reference from the page snapshot
  * doubleClick: boolean - Whether to perform a double click instead of a single click
  * button: string - Button to click, defaults to left
  * modifiers: array - Modifier keys to press

###  Drag mouse

**Tool name**: browser_drag
**Full name**: mcp__playwright__browser_drag

**Description**:
Perform drag and drop between two elements

**Parameters**:
  * startElement (required): string - Human-readable source element description used to obtain the permission to interact with the element
  * startRef (required): string - Exact source element reference from the page snapshot
  * endElement (required): string - Human-readable target element description used to obtain the permission to interact with the element
  * endRef (required): string - Exact target element reference from the page snapshot

### Hover mouse

**Tool name**: browser_hover
**Full name**: mcp__playwright__browser_hover

**Description**:
Hover over element on page

**Parameters**:
  * element (required): string - Human-readable element description used to obtain permission to interact with the element
  * ref (required): string - Exact target element reference from the page snapshot

### Select option

**Tool name**: browser_select_option
**Full name**: mcp__playwright__browser_select_option

**Description**:
Select an option in a dropdown

**Parameters**:
  * element (required): string - Human-readable element description used to obtain permission to interact with the element
  * ref (required): string - Exact target element reference from the page snapshot
  * values (required): array - Array of values to select in the dropdown. This can be a single value or multiple values.

### Manage tabs
**Tool name**: browser_tabs
**Full name**: mcp__playwright__browser_tabs

**Description**:
List, create, close, or select a browser tab.

**Parameters**:
* action (required): string - Operation to perform
* index: number - Tab index, used for close/select. If omitted for close, current tab is closed.

### Wait for
**Tool name**: browser_wait_for
**Full name**: mcp__playwright__browser_wait_for

**Description**:
Wait for text to appear or disappear or a specified time to pass

**Parameters**:
  * time: number - The time to wait in seconds
  * text: string - The text to wait for
  * textGone: string - The text to wait for to disappear
