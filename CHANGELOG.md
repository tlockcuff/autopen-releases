# Changelog

What changed in each version of Autopen.

## 0.2.4 (2026-10-02)

#### Improvements

- Quitting no longer waits on the peer swarm

#### Fixes

- The page no longer sticks on screen after leaving a board
- Gradients fade like the browser's, and translated elements keep exact text

## 0.2.3 (2026-10-02)

#### Fixes

- Opening a board with a saved viewport no longer crashes the app

## 0.2.2 (2026-10-02)

#### New Features

- Board context notes agents read and update
- Run board agents as the user's full Claude Code
- Steer a running agent with messages sent mid-run
- What's new shows the release notes after an update
- Delete, search and sort boards on the home screen
- Phone and web render image assets, fetched from board peers and cached in IndexedDB
- Code export writes the board's image assets beside the pages
- Per-board asset folders, peer fetch, migration of http and data: fills, and ingestion for paste, screenshots and the image field
- .pen import stores relative image files as board assets
- Store captured page images as assets, large canvas and video frames included
- Write used image assets beside HTML and React exports
- Never fetch images at render time; report missing assets and redraw when they arrive
- Asset exchange: peers fetch missing image bytes in sealed, hash-checked chunks
- Store images as content-addressed assets: Generate results, data: and http fills, and asset sources
- Asset urls, image sniffing and an image url walker for fills
- Undo agent runs in one step, global design guidelines, and an update notice
- Watch agent browsers live, and close them when their run or session ends
- PDF pages from each frame's HTML export, with real text and vector shapes
- Images settings with sealed provider keys
- Shader fill problems, lint and ShaderUrl
- Inline relative shader files on .pen import
- Animate @time and @mouse shader fills
- Shader fill kind in the properties panel
- Run shader fills with an inline WebGL runner
- Shader fills via GLSL ES 1.0 to SkSL translation
- Pin Date to the epoch in UTC inside scripts
- Run layout-sized scripts at their laid-out size
- Import .pen libraries as boards and wire their aliases
- Generate svg, vectorize-image and background kinds
- Mesh fills and image crop controls in the properties panel
- One-shot claude text helper
- Read hand-written SVG paint in svgToPaths
- Import boards as component libraries
- Edit script inputs and source in the properties panel
- Load the script runtime with CanvasKit on desktop, iOS and web
- Export image crops and mesh gradient fills
- Crop image fills and draw mesh gradient fills
- Export library components like local ones
- Keep script nodes from .pen files, inlining their source
- Export script output as absolutely placed nodes
- Insert, read and diagnose script nodes
- Script nodes that generate children from JavaScript
- Insert, read and render library instances
- Ten marketing-leaning style archetypes
- Board imports and a component source for shared libraries

#### Improvements

- Asset scan looks only at nodes changed since the last one
- Execute stages only the touched frame, so agent calls stop stalling the main process

#### Fixes

- An image landing after its board was deleted no longer recreates the board folder
- Board thumbnails redraw when an image arrives
- Keep fill type names readable in a narrow panel
- Allow .pen libraries from sibling folders
- Keep .pen side-file reads inside the file's folder
- Fetch board image urls through the SSRF guard
- Run the background model without ORT's memory arena
- Load CanvasKit lazily in the shader fields
- Fetch doc-provided image urls through safeFetchImage
- Load CanvasKit lazily from the script panel

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
