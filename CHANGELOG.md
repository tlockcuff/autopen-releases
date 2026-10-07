# Changelog

What changed in each version of Autopen.

## 0.2.16 (2026-10-07)

#### New Features

- Home is organized around spaces, pins and a Move popover that says what a move will do
- Home remembers the rows you pinned to the sidebar and the folders you moved boards into lately
- A new board can be made straight into a folder, and a board on this computer can be renamed or duplicated
- A board records which computers have it, so Home can tell when a shared board is still only yours
- New boards have a home: Drafts sits at the top of the shared list, where it can't be renamed, moved or deleted

#### Fixes

- New board lays its fields out like Settings, the Move popover stays in the window as it grows, and the level you are at is a destination in the folder picker

## 0.2.15 (2026-10-06)

#### New Features

- A frame an agent grows into its neighbours pushes everything past its old edge aside in the same update, so nothing is ever designed underneath another frame

#### Fixes

- An image whose bytes arrive while its frame is still building draws without a reload

## 0.2.14 (2026-10-06)

#### New Features

- Renaming a listed board renames it on the list for everyone, whoever renames it, and Home shows the list's name
- Opening a board says Opening board…, and a big one says Loading board… until its first draw settles
- Home opens with Recent, the boards last opened on this computer, as many as fill one row

#### Fixes

- The toolbar sits above a selection's quick actions when they reach the bottom of the canvas
- The viewer draws a board's Google fonts, served by the relay as the same TTFs the desktop app uses, instead of falling back to Inter
- A board being joined keeps the name it was listed under and says Joining… with a spinner, instead of being renamed Joining…

## 0.2.13 (2026-10-06)

#### New Features

- Home files boards in nested folders, in a Personal tree on this computer and the directory's tree for everyone signed in; Move to…, drag and drop, a breadcrumb, folder search, and delete only when empty
- The deletion marker is a hint to re-read the list, never the licence to delete
- The person who shared a board to the directory can delete it for everyone
- Releases cut themselves: once CI passes on main with a feat, fix or perf since the last tag and main has settled for 15 minutes, auto-release tags the next version and starts the release
- Importing a Figma file says how far it has got, and what landed
- Home lists the directory beside Personal boards, and Settings shows the account
- Windows read the directory, sign in and share through ipc, and hear every change
- A board directory a fork fills in, which lists an organization's boards behind sign-in
- APP_ICONS points a build at its own icon set, and scripts/icons.ts --out draws one recolored and named for that app
- Verify:figma checks the import against Figma's own render
- File > Import Figma File… opens a .fig as a new board
- Paste a Figma selection, or drop a .fig file, on the canvas
- Turn a Figma scene into editable layers
- Read Figma files and copied Figma selections
- APP_NAME, APP_ID, APP_SCHEME and APP_MCP_PORT make a separate app that installs and runs beside Autopen, with its own data, keychain entry, invite links, MCP port and updater cache
- The SKIP_IOS variable leaves the iPhone build out of a release
- RELAY_URL and VIEW_ORIGIN variables point a build at another relay and browser viewer
- The releases repository comes from the RELEASES_REPO variable, so a downstream copy publishes and updates from its own

#### Fixes

- A board is republished to the directory only when renamed on this device, so a second device never publishes a joining placeholder or brings back an unshared board
- A big board opens fitted to what has built so far, instead of at 100% until every image decodes
- One import note per kind, with how many layers it happened to
- A Figma file imports every layer, not the first 5,000
- One board letting go of an image no longer takes it from another
- A canvas keeps photos at screen size, and gives them back when the board closes
- A board of big photos no longer takes the canvas down
- A directory that could not be read says so above its boards
- Publishing to a releases repository without a CHANGELOG creates one; the README and CHANGELOG carry the app's name, and the README leaves out TestFlight when SKIP_IOS is set
- Read Figma's order keys by their bytes, and guard untrusted parents
- A zero-width Figma stroke draws nothing, and one effect per layer
- Place Figma pages from the boxes Figma measured
- A paste with html but no text still reads the system clipboard

## 0.2.12 (2026-10-05)

#### New Features

- The agent pane header names the agent you're talking to, with one pill for who needs you; Cmd+K lists every agent, Cmd+1 to 9 jump to one, right-click deletes, and the prompt takes pasted, dropped or picked images and files
- View > Toggle Sidebars and Toolbar (Cmd+\) hides both side panels and the tool bar for a clear canvas
- Zooming is gentler: buttons and shortcuts step 10% and pinch or Cmd+scroll moves in smaller increments
- The agent prompt, quick ask and notes check spelling, with suggestions and Add to Dictionary on right-click
- Agent names are four letters at most, each with its own initial, so they fit the switcher and badges
- Agent prompts carry attached images, which Claude sees, and files, which it reads from disk
- Drop image and SVG files on the canvas to place them where they land; pasting takes WebP and GIF too
- Agent runs have no turn limit, and the Max turns setting is gone
- Presentations show a slide's composition full screen, start it once loaded and warmed up, play its soundtrack, and add play, pause and replay; a script measures playback smoothness

#### Fixes

- SVGs keep colors set in <style> rules, so dropped or pasted logos from Illustrator and Figma exports aren't black

## 0.2.11 (2026-10-05)

#### New Features

- Claude setup can update an old CLI and open a terminal for a manual install
- Vector paths are sized to their own shape and picked by their outline, so clicks reach what's under empty space in vector art
- Reopening a board returns to where its camera was left
- Compositions play their soundtrack on the canvas, following play, pause, scrubbing and loops
- MP4 exports carry the composition's soundtrack, mixed with fades and volume and encoded to AAC
- Compositions hold audio clips stored as board assets, from https, data or local file urls
- TakeScreenshot filmstrip, one labelled grid of a composition's frames to judge pacing
- Tuned springs, and blur, corner radius, shadow and gradient fills that animate
- Icons take a stroke outline so they read on any background
- Show a composition's play bar only while it is selected, playing or fills the view
- Warn when motion can never show, keep connector lines and their motion through Connect redraws, and guide presets for travel, grow, type, count, pulse and sequencing
- Motion that follows a path, grows from an origin, types or counts text, repeats tracks, and starts at composition markers or absolute times
- Motion channels for morphing path shapes (geometry), revealing filled art from an edge (wipe) and marching dashes (dashOffset), with guide presets to draw SVG art piece by piece
- Video exports show frame-by-frame progress with Cancel, in the dialog or floating over the canvas
- Follow a person or an agent from their avatar or agent card; the camera tracks their view or cursor until you move it
- Export dialog groups formats as image, video and code tiles with per-format settings, PNG at 3x, and a summary of what it will write
- An export button under the selection's sparkle writes just those layers as PNG, PDF, video or code
- Present opens the board as a slideshow in the browser or copies its presentation link
- Presentation links show the board as slides, one frame or section card at a time, with keys, fullscreen and auto-playing compositions
- Presentation links, /p/<board>#<secret>, parsed beside view links
- /motion skill for Remotion-style slides, videos and GIFs, with presets, timing rules and an animated build for diagrams
- Play, pause and scrub compositions on the canvas
- Export writes compositions as MP4 or GIF through the desktop's video encoder
- Export compositions as H.264 MP4 and GIF, rendered frame by frame and encoded with WebCodecs in a hidden window
- TakeScreenshot shows compositions at chosen times, and motion or timeline values that can't play come back as warnings
- Compositions and keyframe motion: frames with a timeline play their children's tracks (offset, scale, rotation, opacity, color, stroke draw-on) at a playhead

#### Fixes

- Local soundtrack files load only as audio from allowed folders (~/Music, ~/Downloads, ~/Desktop by default)
- DrawArt skips empty fill lists and can sort art into drawing order; guide covers springs, curves and the new channels
- A composition nested in another plays on the outer clock from its own start, and screenshots or exports of it use its own time
- Timing warnings fire for calls streamed onto the board, and a scene that fades out counts as ended
- Only frames of headings and full-size cards split into pages; a screen with its own content, like a dashboard, stays whole
- UiScale lives in its own module, so importing a dropdown no longer loads the window bridge in tests

## 0.2.10 (2026-10-05)

#### Fixes

- With a saved viewport, the page view no longer covers the sidebar and canvas before a page loads

## 0.2.9 (2026-10-05)

#### New Features

- Right-click text menu with cut, copy, paste and select all for fields and selected text
- App-styled dropdowns replace native selects; verify scripts drive them with choose and optionLabels

## 0.2.8 (2026-10-05)

#### New Features

- PDF export splits section frames into a page per diagram, fits pages to Letter or A4, and adds bookmarks and a title
- Outside MCP clients build live: whole execute calls replay statement by statement, paced, under a cursor named for the client
- /diagram is the one diagram slash skill; /architecture removed
- Connect reroutes crossing edges against the finished layout and keeps the route that crosses less; architecture example is an order-to-cash system
- 43 more diagram type references, from sequence and swimlane to Sankey, Wardley and axonometric plans
- Connect gains UML end marks, end labels, dashed any style, zone endpoints, per-type budgets and remembered options; sides chosen around obstacles; no fonts pending without a font source
- Connect draws self-loops, takes arrow end/both/none, and reports when fonts were still loading; harness warms diagram fonts
- Design-first diagram guide adapted from diagram-design, architecture reference on Connect, /diagram slash skill
- Connect routes right-angle connectors around nodes and reports broken connector rules; strokeDash for dashed strokes
- Sub-agent and code-exploration steps roll up into expandable groups with real labels; a typed /skill shows as a link in the composer
- /architecture slash skill; slash skills name their own docs and instruction
- Keys you enter can be shared with everyone on a board
- A new Canvas setting makes the scroll wheel zoom instead of pan
- Architecture diagram guide with routed, numbered edges between system cards
- Cmd+N starts a new conversation; New Board moves to Cmd+Alt+N
- Clicking the version opens the changelog, every release newest first, and it opens offline too
- Toolbar buttons show a real tooltip with the shortcut
- Board notes split into shared notes and this device's own, and agent cursors show as soon as a run is queued
- Draw and edit vector paths with the pen tool, and combine or flatten shapes
- A pen tool and an overlay for vector anchors and handles
- Shape outlines for path operations
- Align and distribute layers from the properties panel
- One key table for every shortcut, with Figma's flip, frame, auto layout, selection, rename, zoom and Alt measuring
- Align, distribute, flip and auto layout worked out from layer boxes
- Polygon and note tools, and red distance lines for measuring
- A guide for turning a codebase into tokens, components and screens
- Boards can point at a code folder agents read first
- Set a frame's theme, and bind number variables to gap, padding, radius and font size
- Edit light and dark variables in a table, with theme axes you can add and rename
- A vector path model that reads and writes svg path data
- Runs open the board's code folder and are told to design from it
- Boards keep their theme axes, and variables rename and retheme in one step

#### Fixes

- Connect ports snap to the half-pixel grid so end segments stay straight; references use end labels, UML marks, self-loops, zone endpoints and remembered options
- Only the boards you chose to share a key on get its replacement
- Agent steps skip templated layer names like ${name} icon instead of showing the code
- Cmd+C over selected text copies the text, not the layers selected on the canvas
- Icons sit dead center in small icon buttons
- The chip's remove button highlights in the chip's own color
- Dialogs opened from the top bar scroll again, instead of acting as the window's drag handle
- The selected-layer chip's remove button has the same breathing room as its label
- The linked code folder sits in the This device notes card
- The remove button on a selected-layer chip sits inside its rounded end
- The context menu opens at the pointer at any interface size
- Text being edited keeps its variable colors and sizes, as the canvas draws it

## 0.2.7 (2026-10-02)

#### New Features

- Ask for a quick change on any layer, and watch the agents working in the corner
- Agents organize a board in one step with Arrange
- Brandfetch lookups survive restarts
- Brandfetch lookups can be kept in a store across restarts
- OpenAI and Gemini keys move to Integrations and are checked before saving
- Integrations in Settings, with Unsplash moved there and Brandfetch added
- Agents on this desktop can use the Brandfetch key
- Get_brand tool and docs for putting real brands in designs
- Generate("logo", nodeId, domain) puts a real brand's logo on the board
- Brandfetch client for real brand logos, colors and fonts

#### Fixes

- Agents put things where your selection points

## 0.2.6 (2026-10-02)

#### New Features

- The agent builds designs layer by layer in front of you

#### Fixes

- Agent steps read in plain words instead of showing snippet code

## 0.2.5 (2026-10-02)

#### New Features

- Pasting SVG markup, like Figma's Copy as SVG, makes vector layers
- Watch the agent design live, like pen.dev

#### Improvements

- Clicks get through while a large board opens

#### Fixes

- A copy of this desktop's data no longer marks the original's live runs stale
- Agents stay on their board and make new artboards there, not new boards
- A relay whose DNS hangs no longer stalls fonts and every other lookup
- Text being edited keeps its place in layout
- The text editor opens over its text at any interface size

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
