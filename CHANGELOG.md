# Changelog

What changed in each version of Autopen.

## 0.2.1 (2026-10-02)

#### New Features

- Collapse the properties pane

#### Improvements

- Draw zoomed-out frames from cached textures

#### Fixes

- Board log truncates on Windows

## 0.2.0 (2026-10-02)

#### New Features

- Markdown in the Agent panel, own runs only, and appearance settings
- Runs are owned by the desktop that ran them; recover runs a crashed launch left behind
- Import pen.dev .pen files as new boards
- Delete conversations from the Agent tab
- Sub-agent cursors wait on their frame from the start; labels follow off-canvas tools
- FindEmptySpace steers clear of spots other agents just found
- Conversations in the Agent tab, with sub-agents nested under their lead
- Spawn_agents and wait_agents start parallel sub-agent runs with their own cursors
- Named agent cursors per run that follow reads and edits, tinted frame shimmer per agent
- Read-only browser viewer for view links, hosted as a static-assets Worker at autopen.tlok.dev
- View link button copies a read-only browser link
- Read-only sync sessions that receive a board but never send doc content
- View links for the browser viewer (https://autopen.tlok.dev/b/<boardId>#<secret>)
- A rotate cursor for the ring outside each corner
- Creation tools, resize handles, rotation, snapping, text editing, clipboard and context menu
- Board operation primitives for create, group, reorder and resize
- Handle, rotation and snapping geometry, rotation-aware hit testing
- Fidelity check against Chromium, rotated frames and radial gradient extents
- Browser MCP tool behind an optional host capability, plus its skill guide
- Sidebar browser tab over a sandboxed WebContentsView, with page and element import
- Snapshot to nodes converter, SVG flattening and fixture tests
- Snapshot types, page capture script and CSS value parsing
- Tighter color rows and an instance check in verify-properties
- Verify-properties drives the panel and the export end to end
- Export the board to code or PNG from the top bar
- Send the canvas selection with the Claude prompt
- Properties panel as a section registry with the full node schema
- Carry the sender's selection into the appended system prompt
- Slash-command skill picker in the Agent composer
- Tabbed left sidebar with an always-open Agent tab, resizable panes, CLI-listed models with effort, remembered window bounds

#### Fixes

- All Boards moves to Cmd+Shift+O so Cmd+Shift+B stays the Browser tab
- Paste through the DOM paste event, keep the caret steady, narrow a click inside a multi-selection
- The browsing session loads web pages only, never local files
- Typecheck verify-properties, which reads clip off a node union
- Resolve modern colour syntax, flatten shared-line inline runs, skip hidden content
- Wrap imported text at the width the page wrapped it, and place inline pseudo-elements beside the text
- Clip content reads off by default, matching the canvas and export
- Pass the model picker to the Agent composer

## 0.1.0 (2026-10-02)

First release.
