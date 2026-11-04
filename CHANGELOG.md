# Changelog

What changed in each version of Autopen.

## 0.2.40 (2026-11-04)

#### View links play motion and show just the board name

- Motion and video play right on the shared page: a play button, then a bar to pause, scrub and mute
- Plays once and stops on the last frame, with Replay
- The top of a shared page shows only the board name

#### People shows the app version each person is on

- Each row shows the version after the email
- Anyone behind the newest version shows it in amber

#### Data inputs and text measuring for script nodes

- Scripts can take data: a json input holds a list or rows like {label, value}, edited in the panel as a text box with one row per line
- Text that isn't valid JSON is kept out, with a note saying why
- Scripts can measure a label with pencil.measureText to place it exactly, using the same fonts the canvas draws with

#### Scale and recolor drawings

- Agents can scale a logo or imported SVG with everything inside it, so paths, strokes and effects shrink or grow together instead of getting cropped
- Copying a drawing can make it a new size in one step
- Agents can recolor a drawing in one call; line art stays line art and never picks up a fill
- A two-color mark can swap each color for its own new one, including theme colors

#### The properties panel works from the keyboard

- Tab and Shift+Tab move through every field, button, menu and checkbox in the panel and its popovers
- Keyboard focus shows a ring on every control
- Plain keys stay with the panel while it has focus, so Tab no longer selects the next layer
- Enter or Space presses a button; Escape closes a popover and goes back to the button that opened it
- Focus stays in the panel when it redraws

#### Paste to replace

- Right-click Paste to replace, or Mod+Shift+V, puts what is copied in place of each selected layer
- A copied picture fills each image box at its size, keeping its crop, and takes the size of anything else it replaces
- Copied layers land where the replaced ones were, in their place among their siblings

#### A z track restacks a layer among its siblings

- Higher draws in front, others stay at 0 in layer order: a planet can pass behind the sun and come round in front
- Drawing, clicks on the canvas, MP4 and the web export all follow it
- The motion guide shows the orbit

#### Boards with 0px text no longer freeze the app

- A 0px text sent Skia a NaN line height; its paragraph cache then spun forever evicting it, locking the window
- Only finite line heights and underline thicknesses reach Skia now

#### Agents read less to get the same work done

- Get reads 2 levels by default, and a Get visitor only reads as deep as it walks
- Word timings on voiceover lines come back only when asked with words: true
- Organizing a board and cloud voices moved to their own guides, read when needed
- Masks, blend modes, hand-drawn strokes and type settings moved out of the main skill into paint and typography
- The app state lists at most 30 closed boards and rounds positions to a tenth
- Saving board memory answers with its length instead of echoing it back
- Web pages read through the browser come back truncated, with a hint to query one section

#### x/y in auto layout keeps the spot as an absolute layer

- A new layer or copy given x/y inside a row or column now stays where it was placed, as an absolute layer, with a warning
- The warning suggests turning the parent's layout off when several layers need placing

#### Warn when a read came before generated results landed

- A call that waits for generated images or artwork now says when it read a layer whose results had not landed yet, and to read it again in the next call

#### Clearer errors when reading the board

- Get with a list or an object instead of one id now stops with how to read several nodes, instead of quietly returning the whole page
- Get on a page id returns that page with its top-level layers
- Print and console.log errors now point to Print

#### Dashes on brush and hand-drawn strokes are even

- Dashed brush strokes and width profiles now show their dashes; before, the dashes were dropped and only the brush's own random breaks showed
- Dashes on wobbly (dynamic) strokes are measured along the line itself, so they stay even however much it wobbles
- A brush's own random breaks are left out when the stroke is dashed, so the dashes are the only gaps
- PNG, PDF and video exports match the canvas

#### Markers and voice lines move with the scenes transitions move

- Adding a transition (one cut or every cut) moves the markers and voice lines in each scene along with it
- Markers between scenes or after the last scene now move with the scene before them instead of staying put
- Voice lines timed in seconds follow their scene too, so narration no longer drifts after scenes shift
- The same goes for dragging, lengthening, reordering, deleting and freezing scenes on the timeline

#### Stock photos match the search better, sounds come from Openverse

- Generate stock picks among the few most relevant photos instead of whichever fits the frame's shape best, so a far-down match no longer wins
- Public domain stock skips clip art, cutouts and drawings
- find_media searches Openverse for music and sound effects by default, where Commons found little
- The generate guide shows how to see thumbnails and choose a photo yourself with find_media

#### Refuse image adjustments written as percents

- Insert and Update refuse an image adjustment past -1 to 1 instead of blowing the photo out
- The message names the fraction meant, as in "contrast: 20 looks like a percent; use 0.2"
- An unknown adjustment such as brightness points at the one that does that job

#### Connectors cross zones drawn behind their nodes

- A zone or lane drawn as its own frame behind the nodes no longer blocks connectors, as long as it holds a connected node
- A frame on top of the nodes, or one that only partly covers a node, still blocks

#### Agents' x/y placement is kept or refused, never quietly moved

- A new frame with no layout whose children all have x/y keeps them where they were placed
- x/y on a new layer inside auto layout now stops the change and says how to fix it, instead of a warning after the layer was moved
- A frame with no layout counts as a row for this check, as it does on the canvas
- Copying into auto layout drops the original's position instead of warning about it
- Arrange refuses children of a frame with no layout, which it could never move

#### Cropping a picture in a grid keeps the box filling its spot

- Crop mode only saves a size the layer holds as its own number, never one set by fill, hug or a variable
- Crop handles hide on a side the layout sizes; the picture still pans

#### Connector parts keep their ids, and clearer motion warnings

- A connector's arrowhead, marker and labels keep their ids when Connect redraws, like its line
- Warns when a fade starts from opacity 0, which keeps the layer hidden
- Warns when x or y keyframes repeat the layer's position instead of offsetting it
- strokeJoin and lineCap point at strokeLinejoin and strokeLinecap; audio on a layer points at the composition's timeline

#### Long video exports finish in the background

- An agent's MP4, GIF or deck export still rendering after two minutes keeps going and is reported on a later call
- WaitForGenerate waits for it, at most 240 s, under the MCP reply timeout

#### A layer over whole scenes is an overlay, not a scene

- Transitions and ripples no longer move a progress bar or background that runs over the scenes
- The motion guide says so

#### The folder path keeps its height over long folder lists

- Library > folder no longer slides under the type tabs

#### The chart legend gets its own row

- Many people no longer push the legend off the card or hide Split by
- Tool calls and per day stay on one line

## 0.2.39 (2026-11-04)

#### Photo libraries (Nextcloud) for everyone

- Connect a library and photo servers show in the Media tab and Settings for everyone, no early feature needed
- Agents see connected libraries in every run
- Early features stay ready for the next one; the admin section hides while there are none

#### scrollbars, opening links on the canvas, and editing fixes

- The board has thin scrollbars that grow on hover
- Resting on a link or a typed-out web address on the canvas offers to open it
- Unlinking a text's own link unlinks all of it; only valid web addresses count as links
- Double-clicking a selected frame's background crops its image
- Content section has an Edit on the canvas button
- Pasting next to a chip in the chat box pastes into the box
- The Export dialog is larger

#### What each board spent on images and voice, made against used

- Usage shows each board's and person's image and voice spend, with how much of it the board still uses
- Download the spend as a CSV

#### A company sign-in signs footage in on its own

- A directory provider can hand out a relay token; the desktop trades it for a footage ticket with no browser
- Signed in to the directory means signed in for footage; Apple stays the core sign-in

#### Clips reach the board while their uploader is offline

- Each desktop puts the clips it has on the relay in the background, two at a time, resuming after a quit
- Someone opening the board later gets a clip from the relay when nobody online has it
- The clip bar says Sharing N% while it goes up; nothing new to choose
- A board past 80% of its footage storage gets a notice, and a clear one when it's full
- Admins can change a board's footage limit (API only, Settings row to come)
- Sign in with Apple plumbing: asked only when a clip needs the relay

#### An in-app right-click menu for text you are editing

- Cut, copy, paste, bold, italic, underline, strikethrough, lists, case and links
- Spelling suggestions and Add to Dictionary in the same menu
- Italic is no longer greyed out before the font list loads
- Bold, italic and undo show at once, even in big frames
- Strikethrough on Shift+Cmd+X

#### Footage reaches people from the relay when nobody has it

- Shared copies upload to the relay in sealed 4 MB chunks, bound to the copy's hash and place
- Uploads resume where they stopped; two people uploading one file meet in the middle
- A clip nobody online has arrives from the relay in order, even while it's still uploading
- Peers stay the fast path; without sign-in footage stays peer to peer

#### Footage in R2, sealed, behind Sign in with Apple

- Rooms keep a ledger of their footage; sealed 4 MB chunks live in R2 under footage/<room>/<id>/<n>
- Every footage request needs a session ticket the relay signs after checking an Apple identity token
- Limits per board (100 GB, admins can change), per uploader per day, and for the whole relay
- Footage no board uses is deleted after 14 days; a board deleted for everyone takes its footage
- Local relay with real Workers runtime and local R2 for tests (packages/relay/src/local.ts)

#### Type settings, lists, and editing that matches the canvas

- Type settings popover from the Typography header: Basics and Details
- Decoration style, thickness, color and offset
- Small caps, number styles, ligatures and stylistic sets the font has
- Vertical trim, paragraph spacing and indent, truncate to max lines
- Bulleted and numbered lists; type "- " or "1. " to start one
- Editing text shows one copy, one outline, and wraps like the canvas
- Exports carry the new type settings to SVG, HTML and React

#### A shorter right-click menu with submenus

- Rows that don't fit the selection are left out instead of grayed
- Copy as › holds PNG, SVG and HTML; Copy link to layer stays in the main menu
- Arrange › holds Bring to front, Bring forward, Send backward and Send to back
- Transform › holds the flips and 90° turns; on a picture the turns keep it upright
- Image › holds crop, colors, background edits, vectorize, trim and save
- Select layer › starts with Go to layer and Select parent, then the layers under the cursor
- One Flatten row; Union, Subtract, Intersect and Exclude move into Boolean ›

#### AI image spend in Usage, an OpenAI cap, and limits on agents

- Every OpenAI image (Generate ai, replace background) records its cost on its board, priced from the tokens billed
- Settings > Usage gets an Images tile and column; the Board tab shows a board's AI image spend
- Voice and Images cells in the boards table show cost only
- The OpenAI key takes a monthly cap in Settings > Integrations; images stop before passing it
- Agents start at most 4 AI images a call and 20 per board an hour, and are told images cost money

#### Right-click menus, an empty start, and Openverse keys for the whole company

- The Media tab opens on an empty state and loads nothing until you search
- Right-click a result: Add to canvas, Fill selection or Replace image, About, Open original, Reveal in Finder; sounds get Play and Add at playhead
- The spinner on a playing sound's play button is white
- Admins can share their Openverse keys with everyone in the company; members can't connect their own
- Adjust colors… opens the image fill's picker on its sliders again
- The selection bar's export button opens the Export dialog on the selection, and clicks inside it no longer reset it
- New conversation and Cmd/Ctrl+N put the cursor in the composer
- The timeline clip style builds whole again

#### A cleaner fill picker that opens beside the panel

- The picker opens left of the right panel, level with the row, as in Figma
- Image fill: a preview to click or drop a file on, a Link field, Crop and Adjust groups with their resets
- Sliders line up in fixed columns; adjust sliders fill out from 0 and a double-click on a label resets one
- Gradients get Reverse stops beside the angle; mesh swatches fill the width
- Shader labels sit in a left column, Source says what the shader reads, and color opacity no longer clips

#### Controls for the CapCut extras

- Transition chip on every cut; a transition shows as a shaded band, half on each clip
- Picker anchored at its cut, with thumbnails of the two clips for every kind; Zoom blur, Whip, Spin, Glitch and Light leak tagged new
- Drag a transition's edges to set its length, stopping at a red line at half the shorter clip
- Transition section in the right panel: live preview, kind, length, direction, ease, Use on every cut, Back to a plain cut
- Clip menu: Freeze this frame (⇧F), Reverse and Replace clip, beside Split, Duplicate and Delete
- Playback section: Reverse switch, Freeze this frame and the hold length
- Holds show a snowflake badge, reversed clips a Reversed badge; their sound lane says why it's muted
- Beats section for music: Find beats, tempo and count, Snap to beats, Cut to the beat with every bar, beat or 2 bars
- Beat ticks on the Audio lane, taller on each bar; scene edge drags snap to beats with a tip
- Caption style: Animation tiles (None, Highlight, Pop, Both, Typewriter), Highlight color, a preview that plays
- Look row for clips and image fills: swatches of its own frame, amount, what it's built from, Use on every clip
- Look badge on clip bars; duplicated scenes start with a plain cut

#### Wikimedia Commons in the Media tab

- Free to use lists Wikimedia Commons next to Openverse, which stays the default
- Commons searches All, Images, Sounds and Video; Openverse's Video says it has images and sounds only
- Video results are poster tiles with their length, and drop on the canvas, a shape or the timeline with their credit
- Sound rows draw flat without a waveform; slow line and unavailable card name the source
- Window calls move to free:* and route by url; verify-commons.ts drives a fake Commons and --live

#### Wikimedia Commons as a public domain source

- commons.ts searches images, sounds and videos, CC0 or public domain only via structured data
- Licence and restrictions are checked at search and again at import, like Openverse
- Videos come from the largest VP9 WebM transcode up to 1080p and 500 MB, never the original
- ingestAsset takes commons: image and sound urls; find_media searches Commons by default and lists videos
- safeFetchAsset takes a user agent, for Wikimedia's client policy

#### WebM files get shared copies

- packages/doc webm.ts demuxes VP9/VP8 and Opus into the same movie the MP4 reader gives
- probeFileAsync reads WebM too, so the existing VP9-capable transcode makes its H.264 copy
- Laced blocks leave their track unread; agent snippets still refuse WebM by name

#### Folders for everyone, lit drop lanes, folder sound waveforms

- Your files and Add a folder… show in the Media tab for everyone; Nextcloud (Connect a library…) stays an early feature
- A sound dragged over the timeline lights the audio lane, where it lands, even over the Main track
- A clip or image dragged over the Main track or the audio lane lights the Main track
- The lit lane clears when the drag ends
- Sounds from a folder show their length and waveform

#### Agent calls, captions and beats for the CapCut extras

- SetTransition, UseTransition, FreezeFrame, DetectBeats and CutToBeat in execute
- DetectBeats decodes the music in the media window and lands beats, bpm and downbeat on the clip
- MP4 captions and the caption preview share one caption kernel; highlight, pop, both and typewriter burn in
- Motion, voiceover and execute guides document transitions, reverse, looks, freeze, beats and caption animation
- verify-extras.ts exports a composition with every extra and checks its frames

#### Decode reversed clips without starting over each frame

- ClipDecoder keeps the eight frames before a backward ask as bitmaps, freeing the decoder's own
- 90 reversed frames in GOPs of 30 decode 247 frames instead of 1395

#### Draw transitions, looks and reverse everywhere

- Canvas, screenshots and MP4 frames sample each scene's transition part at draw time
- Zoom blur and glitch run the scene through a runtime shader; light leak screens a warm glow; whip smears on one axis
- Looks join adjustments in one color matrix on image and video fills; image looks bake into HTML, SVG and React
- HTML export plays transitions with the runner's kernel and seeks reversed clips frame by frame
- Kitchen-sink composition gains a crossfade transition, a teal look and highlighted captions

#### CapCut extras data model

- Transitions stored once on the incoming scene (motion.transition), 11 kinds, sampled at draw time
- Main track keeps each transition cut overlapping by its length, capped at half the shorter scene
- Use one transition on every cut; legacy keyframe transitions read and upgraded
- Reverse flag on clips: source runs backwards, sound muted, splits stay continuous
- Freeze frame insert: split and hold the cut's moment (1 s, or a bar with beats)
- Beat detection from samples, beats on music clips, snap and cut to the beat
- Caption animations (highlight, pop, both, typewriter) with per-word timing and a shared caption kernel
- Eight looks built from image adjustments, with an amount

#### Double-click a marker to rename it

- Enter or a click away renames it, and every layer and clip timed to it follows, offsets kept, in one undo step
- Spaces become underscores; a name that's taken or can't be a marker stays red; Escape keeps the old name

#### Nudge a reframed clip's crop on the canvas

- Crop mode opens on a clip layer and shows the frame at the playhead
- On an Auto reframe clip a nudge pins that scene's crop, which reframing never moves
- verify-clip-editing.ts drives the clip editing UI over real footage, with throttled timeline timings

#### Clip bars, clip sound, the clip panel and Make it a video

- Clip bars show a filmstrip of the source moments they play, a speed badge (30×, 0.5×, Curve, Freeze) and Sharing 42% or Up next while a copy is made
- Trim a clip from either edge of its bar; the tip shows the new in or out point and the change, later clips move along
- A Clip sound lane under the Main track draws each clip's waveform, or why it plays silent
- The clip panel: start and length, in and out in the source, Speed (presets, custom, curves with an editable Custom curve), Sound (volume, mute, Duck under voiceover), Media (the file and whether everyone has it) and Fill the frame
- Auto reframe finds each scene's subject from stills and crops around it; crops nudged by hand stay
- Make it a video turns a frame into a composition at 16:9, 9:16 or 1:1, 1080p or 4K
- The Composition section picks its size from the same menu, or a custom one, and its frame rate as 30, 60 or Other
- Video files dropped on the canvas or the timeline land at once; their shared copies are made in the background
- A Split button in the timeline toolbar; narrow docks drop the frame number instead of cutting off the time; narrow clip bars keep their name

#### Clip editing data and media reads

- Trim, retime, speed curve editing and reframe crop helpers in packages/doc video.ts
- Speed curve presets tuned to keep about the clip's length; presets scale with a sped-up clip
- A person can unmute a sped-up clip (muted: false); duck: false keeps a clip's sound under voiceover
- Composition sizes: 16:9, 9:16 and 1:1 at 1080p or 4K (video-sizes.ts)
- Main reads filmstrip stills, a clip's file details and peer sharing progress, and imports dropped video files

#### See the work agents did, not just their tokens

- Runs in Autopen count their tool calls (subagents' too), how long they worked, and whether they failed
- Undoing a finished run counts it as undone
- New Tool calls tile, and a card for where the work happened: in Autopen beside outside sessions
- The chart shows tokens, runs or tool calls, split by person, where it happened, or model
- Agent runs card: how runs ended, agent time, average and longest run, cost per run, cache share and models
- People table: runs, calls in app and outside, tokens and agent time; open a person for their own page
- Boards table gets a Calls column; a board's page gets the chart, runs card and new people table
- Faces: each person's profile photo, else their Gravatar from the organization's list, else their initial

#### Timeline drops go through the Timeline's own drop API

- Sounds, folder videos and images dropped on the timeline are copied onto the board, then placed by dropOnTimeline
- The lanes light up under a drag from the Media tab
- A folder video dropped on the Main track becomes a scene
- A music clip's bar ends with a shorter sound unless it loops
- Agents' Openverse client and the Media tab follow keys connected in Settings

#### The 1080p note names clips whose originals aren't on this Mac

- The Export dialog asks main which clips in the export lack their original here, and shows the note above 1080p
- Who added a clip isn't recorded, so the note says another Mac

#### HTML exports play clips as <video> in step with the timeline

- A video fill becomes a muted <video> layer the motion runner plays at its speed, seeks while paused or past 16x, and stops outside its layer's window
- Speed curves are sampled across their layer; crops, Fill the frame and adjustments are warned about
- Clips' shared copies are written beside the page, or inside a one-file page up to 50 MB
- Layers with only a time window now come and go in HTML exports, as slideshow photos do on the canvas

#### Clips play on the canvas, and compositions keep only what is near the playhead

- A residency manager decodes the images and clip frames a composition draws from its playhead to half a second ahead, lets the rest go, and shows the exact frame when paused or sought
- A 300-photo slideshow past the image budget now plays sharp to the end, holding about 60 MB instead of every photo
- The canvas decodes each clip's shared copy with WebCodecs from samples main reads off disk; frames reach CanvasKit as GPU bitmaps
- A frame still decoding draws the nearest decoded one instead of a gap
- A clip's sound plays with canvas playback at its speed, ducked under voice
- Verify-clip-canvas checks frames on screen, sharpness, colors, sound, and measures playback at full speed and 4x throttled

#### exports, screenshots and filmstrips decode each clip's exact frames

- ClipDecoder (packages/viewer) decodes a clip's frames by index with WebCodecs, going on from the last frame and jumping to a later keyframe instead of decoding through
- Main's hidden media window keeps a decoder per clip for main's and the agent process's renderers; the original when this Mac has it, else the shared copy
- A clip's sound joins the export mix at its speed, ducked under voice; muted, frozen and sped-up clips stay silent
- The export result lists clips drawn from the 1080p shared copy, with a warning
- clipTrackOf, frameTimes, clipSounds and ADTS wrapping in packages/doc
- Verify-clips checks every exported and screenshot frame against the bars the test footage spells, 20 clips back to back and the timelapse scenario

#### Video fills draw the exact source frame

- A video fill paints like an image fill: mode, crop, adjust, opacity, blend, on any shape
- Fill the frame: reframe crops per shot, blur, color or image behind a fitted clip
- frameIndex picks the last frame shown at or before the source time sourceTime gives
- Decoded frames sit in the image cache by frame key; exports, screenshots and filmstrips decode only what each frame draws
- renderFrames names the clips drawn from a shared copy; a clip the device lacks is listed missing

#### The Media tab replaces Images

- Media tab for everyone: Your files, Free to use (Openverse) and Stock (Unsplash) in one grouped menu
- One search box and a type filter: All, Images, Sounds, Video (Video from your own folders)
- Public domain images with badge, credit and a details popover; sounds as rows with play, waveform and length
- Slow and timed-out states for Openverse, nothing found, and Unsplash needing a key
- Drag onto a shape, the canvas or the timeline; double-click adds in view or at the playhead
- Replace on an image fill and a music clip, keeping crop and timing; a Loop toggle for shorter sounds
- Credits from Openverse and Unsplash stay on the fill or clip

#### Openverse browses and draws waveforms; folders hold sounds and videos

- An Openverse search with no words lists popular public domain results
- Results keep their file and size for previews, and peaks() reads a sound's waveform
- Folder libraries list and search sounds and videos when asked, and give a video's file path
- Image fetches no longer get a 406 from Openverse previews

#### A music clip can loop its sound to fill the clip

- AudioClip.loop repeats the sound from its trim until the clip's length (or the composition's end)
- Without it a clip ends with its sound, so a shorter replacement ends the clip early
- Playback, MP4 export and the motion guide all follow the loop

#### One Timeline with the Main track, overlay lanes and rows that open in place

- The motion dock is Timeline | Transcript; Scenes, Layers and the Ripple toggle are gone
- Main track: always ripples (trim, reorder, insert, delete), Alt on a scene's edge runs it into the next, + adds a scene
- The composition grows when the Main track runs past its end; it never shortens by itself
- Overlays sit in lanes packed by stacking order, pinned to the clip under their start, with a pin dot and line
- Dragging an overlay re-pins it to the clip it lands on, or moves it to another lane or New overlay lane
- Scenes and overlays open in place to their layers, animation chips (In, Out, Loop) and keyframe rows, several at once
- Animated only filter; an open scene shows 8 rows then scrolls inside itself ("N more layers · scroll")
- A layer picked on the canvas opens its rows and scrolls to them; double-clicking a scene zooms to it
- ⌘B splits the selected scene or overlay (or the scene under the playhead); a clip's footage starts at the cut
- Scene menu: Duplicate ⌘D, Split at playhead ⌘B, Add scene after, Transition in…, Ask about this scene ⌘J, Delete
- ⌘D and Delete on a selected scene ripple while the dock is open
- The Timing panel shows "Attached to <clip> · Starts 1.0s into it; moves with it" with Detach
- dropOnTimeline and the application/x-autopen-media drag type put sounds, clips and images on a lane
- Pure helpers in sequence.ts: insertScene, deleteScene, clipAt, pinTo, detachPin, packLanes, stackIndexFor, splitLayer, pinsAfterSplit
- Spans resolve pins and are cached per edit; playing redraws only the playhead and time, not the lanes
- verify-timeline.ts and perf-timeline.ts; verify-motion, verify-video-layers and verify-voiceover-ui follow the new dock

#### Agents ask to read a folder, and Settings › Claude lists the folders

- When ImportMedia can't read a folder, the agent asks in the pane: Allow this folder, Only for this request, or Don't allow
- The card shows the folder, its drive and what's in it; your answer applies before the agent tries again
- Settings › Claude lists folders agents can read, every board's, with who allowed each and when, a board filter and Remove
- Agents never ask for a whole disk or home folder

#### Connect your own Openverse keys in Integrations

- An Openverse card in Integrations: works without a key, fewer results until connected
- Connect registers an app with Openverse from your email, then flips to Connected on its own once the emailed link is clicked
- Resend and Cancel while waiting; Replace and Disconnect once connected; paste keys you already have
- Keys are sealed in the keychain and every Openverse search uses them, agents' too; no keys are built into Autopen

#### Music on the timeline, and markers you can delete

- Add music drops a track at the playhead on its own audio lane; drag clips to move them, and Backspace removes one
- The music panel has a Remove button
- A selected marker can be deleted; layers and clips that started at it keep their moment

#### Emoji draw in color

- Text with emoji draws them with Noto Color Emoji on the canvas, in exports and on the phone and web viewers
- The emoji font loads only once some text on the board has emoji

#### Shared copies of videos made in a hidden window

- ImportMedia's videos become 1080p H.264 with AAC: decoded, turned upright and scaled, hardware encoded, muxed to disk as they go
- H.264 that already fits is copied without decoding; PCM and Opus sound become AAC; the recording date carries over
- Stills for ExtractFrames decode each keyframe stretch once, from the original when this desktop has it
- Each board keeps its copies in a media folder, fetches the clips it uses in the background, and takes another board's copy by hard link
- Per-board allowed folders, with IPC and window.autopen calls for Settings › Claude to list, add and remove them
- Verify-media checks it all in the app against ffmpeg's view of the originals

#### Footage syncs peer to peer in windows straight to disk

- MediaExchange asks for 4 MB windows, two in flight, answered in 192 KB chunks read from disk
- The whole file is checked against its hash; a bad one is dropped and asked for again
- One holder answers each window on a relay room; viewers ask but never answer
- The relay passes media frames along and keeps none

#### ImportMedia, VideoInfo and ExtractFrames for agents

- ImportMedia brings images, sound and video from allowed folders by path, glob or list, one entry per file in name order
- Images and sound land as assets at once; videos and images maxSide shrinks get pending urls that become their copies
- A folder outside the allowed ones is refused by its spelling alone and names the folder to allow in Settings › Claude; inside, every failure reads the same
- Allowed folders can differ per board; a local path or http(s) link in a video fill becomes its shared copy
- VideoInfo reads a path, a pending import or a copy on this device; ExtractFrames queues stills
- MediaStore, the originals index and MediaHost for hosts that can decode

#### Video sniffing and an MP4/MOV reader

- sniffVideoType tells MP4, MOV and WebM from images, songs and HEIF stills
- packages/doc/mp4.ts reads the movie box before or after the media: tracks, WebCodecs codec strings and decoder descriptions, sample tables, edit list start, rotation, recording date
- VideoInfo shape and the shared copy's size (long side at most 1920, never larger, even)
- Video fills' urls count as asset urls; videoUrlsOf lists them so footage can sync apart
- Tiny fixture clips: H.264 with AAC, HEVC turned in a MOV, movie box at the end, WebM, M4A

#### Video size, frame rate, codec and quality

- Size: Frame size, 720p, 1080p, 1440p or 4K, drawn at scale so a 1080p composition is sharp at 4K
- Frame rate: 24, 25, 30, 50 or 60
- Codec: H.264, or HEVC where this computer encodes it, at the right level (4K60 H.264 is 5.2)
- Quality: Draft, Good or Best instead of a bitrate
- MP4s are written to disk as they encode, with their index up front; cancel leaves nothing
- The Export dialog remembers your last video settings; quick export and deck export use them
- Agents: Export(comp, 'mp4', path, { size, fps, codec, quality, captions, voice, music }), checked with clear errors

#### Animation cards and a key toggle on every animatable field

- The right panel's Motion section lists one card per animation: grip to reorder, name, In/Out/Loop, length, eye to turn it off, delete on hover
- A card opens to At, Length, Distance, Direction (wipe reads From Left/Right/Top/Bottom), Ease with spring Bounce and Stiffness
- Type cards pick by letter or word; Count cards edit From, To, Decimals, Before/After text and the thousands separator
- The + menu adds animations grouped In, Out (with Untype and Count down) and Loop, plus Ask an agent
- A group's card staggers its children; a child shows it read only with a link back to the group
- X, Y, Rotation, a new Scale field, Opacity, Corner radius, Fill, Stroke, Shadow and Blur each get a key toggle
- Editing an animated property keys it at the playhead; Record keys is gone from the timeline toolbar

#### clips, speed curves, overlay pins and animation switches in the data model

- A video fill puts footage on any shape, with in, speed or a speed curve, volume, loop and Fill the frame
- Speed curve presets (Montage, Hero, Bullet, Flash) keep the whole clip and change its length; sound mutes above 2x
- A freeze frame is the same clip held at one moment, so it keeps its look and exports exactly
- Titles and stickers pin to the clip under them and follow it when the Main track moves, on the canvas and in HTML export
- Animations can be turned off without deleting them, and Count starts from any number and counts down on the way out
- Agents get clear warnings for a bad clip, a pin that can't play, and a freeze frame with no length

#### Agents find and place public domain images and sounds

- find_media searches Openverse for CC0 and public domain images and sounds from sources that review licences
- Agents place openverse: urls in image fills and audio clips; each is checked again and copied onto the board with its credit
- Stock photos without an Unsplash key come from public domain Openverse photos
- Audio clips from a web address now land on the board instead of staying pending

#### Animations stay editable after they are applied

- Layers keep named animations (rise, pop, wipe, pulse and more) with their timing, distance and direction, worked out when drawn instead of baked into keyframes
- Entrances, exits and loops combine on one layer; a stagger on a group plays on each child in turn
- The canvas, video export and HTML export all play them
- Agents write animations by name, and get a clear warning for one that can't play

#### New Features

- Admins see everyone who signed in

#### A call that only reads no longer copies the whole board

- A call reads the live board and makes its staging replica only at its first write
- Get visitors, screenshots, Print, Pages and exports on a new session copy nothing
- On a 97k-node synthetic board, a read-only call in a new session went from 1.2 s and 410 MB of heap to 0.3 s and under 1 MB

#### Copied text pastes into other apps, pictures paste into the selected box

- Copying a text layer copies its words too, linked words followed by where they go
- Pasting a picture with an image box selected fills the box at its size, keeping its crop

#### A clip that arrives late plays without reopening the board

- The canvas now decodes a clip that lands after its composition was drawn, peer to peer or from the relay
- verify-footage.ts: two desktops and a local relay with local R2, end to end

#### Look row lays out, Replace clip for everyone

- Look name and Amount slider sit on one line instead of stacking
- Replace clip… shows whenever you have a folder library

#### Text keeps its exact look while you edit it

- The canvas draws the words as you type; the editor shows only the caret and highlight
- Clicking into a text no longer changes its weight or shifts it
- Typing past the panel edge no longer scrolls the canvas aside
- Japanese and Chinese composition still shows while composing

#### Editing breaks lines exactly where the canvas does

- Clicking into a text no longer moves a word to another line
- The editor loads the same font file the canvas draws with, uploaded fonts too
- The editor no longer picks up the interface's font features

#### Only known decoration styles reach exported CSS

- A made-up decorationStyle on a board can no longer inject CSS or markup into HTML and SVG exports

#### A clip after a transition opens again

- A transition's drag edge covered the next clip's open triangle and name; it now sits over the filmstrip only

#### The app's stylesheet builds again

- A pressed-toggle selector had landed inside the bound-field rule, which broke the CSS build; it's back with the other pressed toggles

#### Typography card back to two sentences

- Drops the note about the dimmed Italic button

#### Follow pages, steady text editing, real font faces

- Following someone takes you to the page they are on
- Editing text no longer opens an empty, collapsed box
- Black and other heavy weights draw the font's real face
- Font style picker lists every face the font has, italics included
- Italic toggle next to Underline and Strikethrough
- Text toggles show when they are on
- Agents lay out posters, posts, slides and ads freely, auto layout for UI

#### The clip panel's length note sits inline again

- "later clips move" after a speed change no longer shows as an empty box on its own line

#### A video dropped on the board plays

- Dropped anywhere but inside a video, a clip becomes a video of its own, the clip's size and frame rate, so it shows its frame, plays and exports instead of sitting there blank
- Several files dropped together play one after another in that video

#### The Ask box is styled again

- Its text box had lost its look when the agent's message box moved to a formatted editor; it sits in the frame like the agent's again

#### Extras verified end to end in the app

- Zoom blur and glitch sample the scene where it sits, not at the board origin
- MP4 captions run the caption kernel, so highlight, pop and typewriter burn in
- Freeze frame settles the next transition against the rest of the clip
- Cut to the beat leaves room for both transitions in every scene
- verify-extras.ts passes: reverse exact, looks, freeze, transitions, captions, screenshot equals MP4

#### Board compaction can no longer crash the app

- Compaction collects in its own utility process, not a worker thread: the worker shared main's 4 GB V8 heap and aborted the whole app with "young object promotion failed" on big boards
- If the compaction process dies, the board is saved as it is and a line goes to main.log
- Closing a board with nothing new since its snapshot skips compaction
- scripts/verify-compaction.ts compacts a board while main's heap is nearly full

#### The transition picker closes when you click away

- A click outside the picker or Escape closes it, like the timeline's menus; clicking another cut still switches to it

#### The transition picker opens at the cut you clicked

- It sat above the whole dock, far from the Main track now that the track is at the bottom; it now opens at its cut, above or below as the window has room

#### Exports check where a folder really is

- /private/tmp is accepted like /tmp, since it's the same folder
- A symlink inside an allowed folder can no longer lead an export outside it

#### The play bar runs the whole video when the Main track is shorter

- Time no scene covers, such as overlays playing on after the last scene, shows as a plain stretch of the bar you can scrub, instead of empty space

#### Add voiceover keeps its text white on hover

- The lane's border and tint still turn the voice color; the label stays readable like Add music's

#### A scene's or overlay's menu opens where you right-click

- At an interface size above 100% the menu opened down and to the right of the pointer

#### The environment note stays with the Claude settings it explains

- On Settings › Claude, "Some of these are set by environment variables" sits above Folders agents can read instead of under it

#### Every video setting fits its column

- The Captions choices no longer run off the edge of the Export dialog; the segment labels shrink to fit

#### A frame's stagger can be edited in the panel

- A frame's animation card has a Stagger field, so a frame an agent staggered can be retimed
- On a frame it plays on the frame itself until a stagger above 0 is set; a group still staggers by default

#### Folders are added and removed in the Images tab

- Each folder in the Images tab's source menu has an × to remove it, and Delete removes the highlighted one
- Settings, Integrations lists photo servers only

#### Conversation files open from the agent's menu

- The paperclip button in the agent pane's header is gone; Files… is in the menu on the agent's name

#### Plan names follow the Max and Ultra rename

- 5x Max shows as Max and 20x Max as Ultra

#### Video frames always go through the canvas

- Raw-byte VideoFrames used 230 MB more at 4K for the same speed
- The dialog keeps HEVC picked while it checks this computer can encode it

#### A board main lets go of is freed, instead of a whole copy kept per reopen

- Closing a board destroys the awareness it made, whose renewal timer kept the doc alive
- Closing a board drops main's layouts of it, held by an export or a share link's copy
- A background agent working on a board no window shows has main reopen it when calls are over 6 s apart: on the 97k-node Autopen board main kept 340 MB per call (379 MB to 3.1 GB in 8 calls) and ran out of heap; now it holds 38 MB between calls

#### A slow Openverse gives up cleanly instead of hanging

- A search gives up after 20 s with a clear error to try again or use another source
- A gateway error is tried once more while time is left
- Recent searches come back from memory, and the same search running twice is asked once

#### Staging replicas no longer pile up until the agent process runs out of memory

- A session lets go of its staging replicas when it ends, and a failed call's at once
- The layout cache drops a replica's or mirror's layout when it goes, instead of holding the last 8 whole boards
- On the 97k-node Autopen board, 24 per-call MCP sessions held the agent heap at 339 MB, where it climbed 310 MB per edit to an OOM

#### A composition's end shows its last frame

- A layer that runs to the end of a composition still shows when the playhead or a filmstrip sits at the end

#### Agents can export to temp folders

- Export writes under the temp folder and /tmp as well as home, so an agent can check its own output

#### Long slideshows export sharp

- Export, screenshots and filmstrips decode only the images each frame draws, so hundreds of photos stay inside the image budget
- Export says how many images it drew below full resolution when one frame alone runs the budget out

#### Unknown fill types are refused

- Insert and Update refuse a fill or stroke type nothing draws, like video, and list the ones that work

#### Agents stop asking which style on a new board

- A board with no style gets plain, neutral designs without a question
- The style card shows only when someone asks for help choosing

## 0.2.38 (2026-11-03)

#### Figma stroke settings, layout guides, new effects and panel polish

- Stroke: Position and Weight row, settings popover with Basic (dash, cap, join,
- Layout guides: grid, columns and rows per frame, drawn in the editor only, ^G toggles.
- Effects: noise, texture, glass and shader, in Figma's menu order. Glass
- Panel: Artboard is its own section with a checkbox, speaker notes under

#### Org view shows cloud voices and everyone, non-admins see only their own

- Voice tile, column and note in the organization's view
- People list of everyone in the organization's view, the same table as a board's page
- Someone at a company who isn't an admin sees only their own devices' usage, from every computer they use

#### Stroke and Speaker notes info cards stay two sentences

- The right panel's Stroke and Speaker notes info cards fit the two-sentence limit again

#### Every signed-in device reports usage, voices and key spend as merged deltas

- Non-admins report too: sending uses Directory.reportScope, viewing keeps teamScope
- Reports merge per key at the most of each number (mergeDeviceUsage), so usage on deleted boards stays counted
- Only changed keys go, at most 3000 a request, remembered in team-usage-sent.json; a new account sends everything
- A failed report is logged and tried again soon
- Reports go when this device's own usage or voice costs change on a board, and on sign-in
- Reports carry cloud voice costs and what each key paid for per board and month
- Outside tool calls count on boards that aren't open
- Company key caps count the person's spend on all their devices (DirectoryUsage.mine)
- usage:mine gives non-admins their own devices' usage

## 0.2.37 (2026-11-03)

#### Fixes

- Swatch edge rings follow the swatch's rounded corners

## 0.2.36 (2026-11-03)

#### Figma-style right panel

- One row per paint and effect, effect popover, short nothing-selected panel
- Nothing selected: Board name, one Variables row that opens the manager, Export.
- Frame head with align row and artboard toggle; Position with rotation and turns; Auto layout with
- Fill and Stroke: one row per paint (the color picker's paint field, then eye and minus). The swatch
- Effects: one row per effect; the row opens a popover with type, blend, position, blur, spread and a
- Export opens the Export dialog on the selection or the page; the dialog loads on first open.
- Help cards: Frame, Appearance and Export replace Layer, Artboard and Corner radius.
- scripts/verify-right-panel.ts covers the new panel; verify-properties, verify-themes, verify-help-panel,

#### Hidden frames stay out of exports, and one bad frame no longer fails the batch

- Hidden frames, and layers inside hidden ones, are left out of PNG, JPEG, video, SVG, PDF and code exports, with a note naming them
- Hidden artboards inside a section no longer show up in the Export list, Present or PDF pages
- A frame that can't be drawn is skipped and named; the rest of the export still saves
- Notes about what was left out show after the export finishes

#### A board opens centered on its content the first time

- Opening a board you were invited to waits for its layers to arrive, then zooms to fit them, including ones that land a moment later
- A page's view is only remembered once its layers have loaded, so an empty first look is never brought back
- A remembered view that shows none of the page zooms to fit instead
- Switching to a page for the first time fits its content the same way

## 0.2.34 (2026-11-03)

#### Fixes

- Tabs sit centered in the header with their icons, as designed

## 0.2.33 (2026-11-03)

#### Link words inside a text

- Highlight words while typing in a text and press Ctrl+K, or right-click and pick Add Link, to link them to a web page or to a frame or page on the board
- The link field suggests the board's frames and pages, and turns allbulkfoods.com/flours into a full web address
- With the caret in linked words, a bar shows where they go, with Open, Edit and Remove
- Linked words look the same as the words around them, as in Figma; hovering them on the canvas names the link
- Clicking a link while presenting, or in a shared view link, opens the web page or goes to the frame
- HTML, React and SVG exports keep the links
- Figma imports keep links on part of a text, and a link on a whole text layer
- Agents can link words with StyleText's href

#### Style part of a text layer, as in Figma

- Highlight words while typing in a text and press Ctrl+B, Ctrl+I or Ctrl+U to bold, italicize or underline just them
- With words highlighted, the properties panel sets font, weight, size, letter spacing, underline, strikethrough and color on those words only; the text stays open and the words stay highlighted
- The panel shows Mixed where the highlighted words, or a whole text, differ
- A style set on a whole text layer applies everywhere in it, as in Figma
- Each style change is one undo step, and undo while typing steps back through them
- Typing, pasting and Change Case keep each word's style where it is
- Text with mixed styles draws, wraps and sizes itself correctly on the canvas, and exports as styled spans to HTML, React and SVG
- Figma imports keep mixed text styles instead of flattening them to one
- Agents can style part of a text with StyleText
- New help guide: Style part of a text

#### Format your message as you type it

- The agent message box takes formatting: Ctrl+B bold, Ctrl+I italic, Ctrl+E or backticks for inline code, Ctrl+K to link selected text (Cmd on Mac)
- Typing "- " or "* " starts a bullet list, "1. " a numbered one, "> " a quote and ``` a code block
- In a list, Enter adds the next item, Enter on an empty item ends the list, and Tab or Shift+Tab indents
- Pasting from a web page or document keeps bold, italic, lists, links and code; pasted markdown keeps its formatting too
- Your sent messages show formatted in the conversation, and the agent receives them as markdown

#### Every Google font, your installed fonts, and Upload font, kept with the board

- The font picker lists the whole Google Fonts catalog, searchable, and stays quick by drawing only the rows in view
- Fonts installed on your computer show in the picker too, each in its own face; picking one stores it with the board so everyone sees it
- Upload font in the picker adds TTF, OTF, TTC, WOFF or WOFF2 files to the board and sets the selected text in it
- Drop font files on the board to add them; selected text switches to the new font
- Collaborators, view links, shared links and exports draw text in the board's own fonts
- The weight list follows the weights each font actually has

#### Place images from a network share, a file or a web address

- Place image (toolbar, File menu, right-click menu, Ctrl+Shift+U) opens the file picker, network locations included; with a shape selected the image fills it
- The Images tab can add a folder on this computer or a network share (\\server\share, mapped drives) as a library to browse, search and drag from
- Settings, Integrations adds a folder by picker or by typing its path
- Pasting an image's web address or a file's path, such as Explorer's Copy as path, places the image
- Dropping one image file on a shape fills it; a link dragged out of a web page places its image

#### Pop the agent conversation out into its own window

- Pop out in the conversation header moves a board's chat into a window of its own, to keep on another screen while the board stays in view
- The sidebar folds to its rail while the chat is out; the Agent tab says where it went, with Show window and Bring back
- Closing that window, or Dock in it, puts the chat back in the sidebar
- The popped-out chat stays live: messages stream in, sending and attachments work, it offers the layers selected on the board and anchors to the page open there
- Clicking work an agent did in it goes there on the board
- It reopens at the size and place it was left, on whichever screen

#### Layer blend modes, as in Figma

- Blend mode now works on any layer: Multiply, Screen, Overlay, Color burn, Color and the rest blend the whole layer with what is beneath it
- The blend mode menu sits beside Opacity in the Layer section, in Figma's order and names, and shows Mixed across a selection
- Frames and groups pass their children's blending through by default; set one to Normal to keep that blending inside it
- Layers that blend on the board blend with each other, never with the canvas behind them
- SVG and HTML exports keep layer blend modes, and Figma and web imports bring them in on the layer instead of its fills

#### Change letter case from the panel or a text selection

- Typography has a case control: UPPERCASE, lowercase, Title Case and Sentence case, for one or many text layers at once, one undo step
- Highlight words while editing text and right-click for Change Case to convert just those words
- Alignment icons in the properties panel no longer shrink to dots in a narrow panel

#### Drag several layers at once in the Layers panel

- Dragging a selected row in Layers carries every selected layer, keeping their order, with a count while you drag
- Dropped into a frame or group they keep their place on the canvas, unless it uses auto layout
- The whole move undoes in one step
- Bring forward, send backward, to front and to back keep several layers in their order
- Ctrl+Shift+] and Ctrl+Shift+[ also bring to front and send to back

#### Preview an image before exporting it

- Export has a Preview row for PNG and SVG that shows exactly what the file will hold, hidden layers, masks and effects included
- The preview follows the chosen format and scale, and redraws a moment after the design changes
- With several layers, it shows the first and says how many there are

#### A milestone shows the person it was made for

- A milestone with no agent on it, such as one marked from your own terminal, now shows the person's avatar and name in the Milestones tab
- New milestones record who they were made for and sync that to everyone on the board; older ones show as before
- list_milestones names that person, so agents can tell whose work a milestone was

#### New Features

- Video is greyed out on a page with no timelines
- Export dialog with Image, Document, Video and Code tabs
- Every font in the picker is drawn in its own face, as is the family in the field

#### Frames set apart inside a holder frame show their names

- Frames spaced apart inside a top-level frame with no auto layout, clear of its edges and of each other, show name labels like screens in a section
- Click one of these names to select the frame, double-click to rename it; the names hide when zoomed out too far to fit
- The agent and the Artboards guide now explain which frames show a name on the canvas

#### Exported pages and SVGs never carry a script link

- HTML, React and SVG exports drop any link that isn't a web, mail or phone address, a relative path, or a place on the board, such as a javascript: link

#### Favorites stays open unless you shut it

- Favorites in the Home sidebar starts open on every page, including inside an account
- Shutting it is remembered on this computer until you open it again

#### New conversation is always the last button in the conversation header

- Pop out and Dock sit just before New conversation

#### A link dragged out of a web page only reaches the public internet

- An image link dragged in from a web page can no longer point at the office network or a file path
- Pasted addresses and paths, the file picker and dropped files still reach network shares

#### PNG files come out at the full size of the picked scale

- A PNG export is now as large as the scale asks, so a 1920 px frame at 2x is 3840 px wide; it was never more than 1000 px
- Copy as PNG is full size too
- An image too big to make (over 16384 px a side or 64 megapixels) says so and asks for a smaller scale

#### Every action undoes in one Ctrl+Z

- Ctrl+Z, Ctrl+Y and Ctrl+Shift+Z on Windows and Linux are handled by the board itself, so undo always reaches it
- Undo still works on the board when a checkbox, slider or color swatch has focus
- Each command is exactly one undo step, however quickly the next one follows
- A drag, resize or rotate stays one undo step even when you pause mid-drag
- Dropping a layer into a frame, and an Alt-drag copy, undo in one step with their move
- Holding an arrow key nudges as one undo step
- Dragging a color picker on the canvas bar, a mesh gradient or a color variable is one undo step

#### Right-click menus near the bottom of the window open upward

- A right-click menu opened low in the window flips up so every option shows, instead of running off the bottom
- Applies to every menu: Home folders and boards, the canvas and layers, pages, tabs, and agent conversations
- Submenus move up to stay on screen, and a menu taller than the window scrolls

#### Mouse back and forward step through library folders

- The mouse's back and forward buttons (and Alt+Left/Right, or a keyboard's Back and Forward keys) now go back and forward through the folders you opened in the Images panel
- They step the in-app browser's pages too while it's open
- They never send the whole window away from the board you're on

#### Grouping layers from an auto layout frame keeps them intact

- Images and rows that fill an auto layout frame keep their size when grouped instead of collapsing or reflowing
- Ungrouping them puts them back filling the frame, as they were before

#### Fixes

- Setting segments fit their labels, so the text sits centered

## 0.2.32 (2026-11-03)

#### A person's cursor shows only on the page they're on

- Someone on another page no longer leaves a cursor on yours, so a duplicated page can't look like a shared one that stopped syncing
- People on older apps, which don't say their page, still show as before

## 0.2.31 (2026-11-03)

#### Clipping masks, as in Figma

- Use as mask (⌥⌘M, or right-click) wraps the selection in a Mask group; its bottom layer masks the rest
- One layer selected becomes a mask over the layers above it; Remove mask turns it off
- Masks clip by their opacity, so any shape works and soft fills give soft edges
- What a mask hides can't be clicked, and the mask has its own icon in Layers
- SVG export keeps masks; HTML export clips to rectangle and ellipse masks
- Masks come through from Figma files, and agents can make them

#### Autopen links itself into Claude Code and the Claude app

- Every start adds Autopen to Claude Code and the Claude desktop app, no clicks
- Claude desktop app chats can see and edit your open boards
- One Settings switch covers both; turning it off unlinks them and stays off
- Someone else's server named autopen is never replaced unasked

#### A chat stays on the page it was sent from

- Each run is anchored to the page open when its latest message was sent; get_app_state reports it as homePage
- Execute calls start on that page every time; UsePage lasts one call unless sticky, and WithPage runs a step elsewhere then comes back
- A message sent from another page moves the chat there, and the agent is told
- An agent's cursor shows only on the page it is working on

## 0.2.30 (2026-11-03)

#### A board reaches the agent process from its files, not a copy of the whole doc

- When an agent first opens a board, main sends what is stored on disk and then only what is newer, instead of encoding the whole board

#### An edit redraws only the frames it touched, even beside animated slides

- One animated slide no longer makes every edit in its section redraw the whole section
- Frames from 16 layers up get a picture of their own, so an edit to one slide leaves the others alone
- A paused animation keeps its picture through edits elsewhere instead of recording again
- A change to a parent frame, such as its theme, now redraws the frames inside it instead of leaving them stale
- Play bars read only each composition's timeline, not the whole layer, on every frame

## 0.2.29 (2026-11-03)

#### Agents run in their own process, so their work never freezes the app

- The MCP server and every agent session run in a utility process; the app's main process only applies their edits
- Clicks, typing and window drags stay responsive while an agent reads or edits a big board
- Undoing an agent's run, streamed edits and their rollback work as before
- If the agent process stops, the app starts it again and the next agent call works

#### A run's end waits for streamed pieces still loading their board

- A piece that arrives while its board is still loading can no longer land after the run ended and stay on the board

#### A cached Google font is written whole before anyone reads it

- Main and the agent process share the font cache, so a font lands under its name only once fully written

## 0.2.28 (2026-11-03)

#### Record Performance Trace, for when Autopen is slow

- Help > Record Performance Trace records every process for up to a minute, then Stop saves one zip to Downloads
- The zip holds a Chrome trace, a main-process CPU profile, and a report of the machine, GPU, memory, frame times and open boards
- Autopen now keeps a log of its own (main.log, two files at most), sent along in the zip
- profile-board.ts takes --src and --throttle to profile a real board from any app's data on a slowed CPU

#### Fixed style offer, Built-in styles or No style

- Agents on a board with no style ask the same offer every time: Built-in styles or No style
- Built-in styles opens the style gallery, and the style picked there answers the agent
- No style lets the agent design plain and neutral without setting a board style
- The agent now hears the picked style's key with the answer
- Builds can add company styles (content/styles/company), offered first and listed first in the gallery

#### Side panels stop rereading the whole board on each edit

- The canvas stays smoother on big boards while an agent works
- Milestones does nothing while its tab is hidden, and formats dates without making a formatter per card
- The page row counts archived layers from an index instead of walking every layer
- The play bar reads only each composition's timeline, and finds their boxes once per redraw, not on every pan frame

#### Bullets right under the subject stay bullets

- What's new splits a commit at its first line, so bullets written with no blank line under the subject still show as bullets

#### A middle-button pan follows the pointer past the canvas edge

- Panning with the middle button keeps going when the pointer leaves the canvas or the window

#### Company style options survive the question check

- A company style offered to the agent keeps its preview instead of showing as a plain option

## 0.2.27 (2026-11-02)

#### Drafts grouped in a Drafts frame, and Cmd+P to go to a page

- Each page's drafts sit together in its Drafts frame, labeled "Drafts" with how many it holds
- Approve and Set aside work on drafts in the Drafts frame; Show archived reveals hidden ones there
- Cmd+P (Ctrl+P) opens the page picker from any tab with search ready

#### Milestone cards, and a Drafts frame on each page

- A run that marks a milestone ends with a card: a picture of the work, a short title and a two-line description
- Runs with several milestones, and the Milestones tab, show compact cards; click one to open its page and zoom to the work
- Agents give each milestone a short title
- On boards that review work, each page keeps its drafts together in one Drafts frame
- Approving a new screen moves it out of the Drafts frame onto the page

#### No special pages; drafts sit beside your work

- New boards start with one page holding the cover frame as their thumbnail; there is no Cover page
- Review first adds no pages: agents put drafts beside the screens they change, labeled Draft
- Approve swaps a draft into the old screen's place and hides the old one as archived
- Set aside hides a draft; Show archived on the page row reveals hidden screens, and Restore brings one back
- Figma files set the frame on their Cover page as the board's thumbnail
- Agents leave variables that approved screens use alone on boards that review work

#### Pages on boards

- A board holds pages; only the open page loads onto the canvas, so big boards stay fast
- The page menu above Layers opens a picker with folders on the left and pages on the right, plus search
- New page, new folder, rename, duplicate, delete, drag to reorder or into a folder
- Move layers to another page from the right-click menu, or drag them onto the page menu
- Cmd+Option+Up and Down step through pages; each page keeps its own view
- New boards start with a Cover page; its 2:1 cover is the board's thumbnail on Home
- Home cards are 2:1, and frames say Set as thumbnail
- Figma files import with their pages, divider pages become folders, and Cover becomes the cover
- Agents work on the page you have open, can switch pages, and can make, move and delete pages and folders
- Find can search all pages; Share and Present links open on your page; the web viewer and phone get a page menu
- Review boards use Drafts and Archive pages: Approve puts a draft in its place, Set aside and Restore move it to and from Archive
- Boards made with the Final, Drafts and Archive frames can be split into pages
- A board opened in a newer Autopen asks to update instead of risking edits

#### New Features

- Quick edits report in the stack, not beside the selection
- Stack of the board's agents at the canvas's bottom right
- Toolbar clearance on either side, toasts can skip a board
- Model of the agents working on a board
- An (i) beside each sidebar tab title opens its clip and guide

#### One card per page

- A milestone whose work is on several pages shows a card for each page, and each card opens its own page
- Worked out as the cards show, so work moved to another page later still lands on the right card

#### Fixes

- A quick edit's hover actions fit on its card

## 0.2.26 (2026-11-02)

#### One Integrations page for every outside service

- Images and Voices fold into Integrations: a grid of cards with each service's logo, grouped by what it powers
- Open a card for its key, monthly cap, this month's spend and on switch; connecting a key turns the service on
- Unsplash and Brandfetch can be turned off on this computer
- With a company, admins set keys from the same cards and everyone else sees them read only
- Phonon's page holds the default voice and Import voice file

## 0.2.25 (2026-11-02)

#### Company keys, early features per person, and photo libraries

- Signed in to a company directory, the app runs only on the company's keys; admins set each key and a monthly cap per person in Integrations, and manage admins on the directory page
- Everyone else sees Integrations, Images and Voices as managed by the company, and only their own usage
- Admins turn early features on per person under Early features on the directory page; they are off for everyone else
- Photo libraries (early feature): an Images tab to browse and search a Nextcloud library, drag photos onto layers or the canvas, and agent tools to find them
- AI images use OpenAI gpt-image-2 only; Gemini is now for voices only, and stock photos need an Unsplash key
- Voice spending caps move to Integrations; Voices links there when a key is missing
- Rename a tab from its right-click menu without switching to it
- Help clips re-recorded

#### Edit links open in the app from chat and mail

- Copy link on Edit now gives a web link (autopen.tlok.dev/join/...) that chat and mail apps keep intact, instead of an autopen:// link they mangled into a broken web address
- Opening it in a browser hands the board to the app, with an Open in Autopen button if the browser asks first
- Join a board, Copy link to layer and agents take both the new link and the old autopen:// one

#### Shift-click in Layers selects the run at that level

- Shift-click adds every layer between the last one clicked and this one, at the clicked layer's level, skipping open children
- Ctrl-click (Cmd-click on Mac) still adds or removes one layer

#### Usage card hides a limit the plan doesn't report

- Plans without a 5-hour limit show only the Weekly row, not an Unknown one
- The chip by Send reads the week when there is no 5-hour limit

## 0.2.24 (2026-11-02)

#### A release never publishes without both update feeds - v0.2.23 shipped Mac-only

- Its Windows build artifact expired before a Mac rerun published
- So Windows update checks failed - Build artifacts keep for 7 days so a later rerun still has both - Publish fails if latest.yml or latest-mac.yml is missing

#### Release smoke tests take turns on the shared Mac

- Core and MoJo releases ran their DMG smoke tests at once on the mini and swapped each other's default keychain, so both failed
- A machine-wide lock now runs one smoke test at a time

## 0.2.23 (2026-11-02)

#### Edit an instance's texts, and Go to layer

- Instance content section lists an instance's texts to edit, with a reset arrow per text
- Double-click a text inside an instance to edit it in place for that instance only
- Go to layer in the right-click menu opens Layers on that layer
- Layers scrolls to the selection; instances and components wear the component icon

#### Present setup is a big dialog with titled slides

- Present opens a dialog over the board, up to 1080x760, instead of a small popover
- Slides show large, numbered and titled, grouped by section, each in its own shape
- "Drag slides to change the order" says how to reorder; Reset shows once it changed
- Escape, the close button or a click outside closes it; Enter still plays
- Snapshots take a margin, 0 for slides so neighbors don't show
- Fix the usage pace tick's CSS comment left out of the last commit

#### The usage pace tick marks where use lands by the reset

- The pace text above each bar is gone; the tick says it on hover
- The tick sits at the projected use at reset, amber when that is close to the limit
- Tooltip: "At your current pace, you'll be at 56% in 3h 4m, when it resets."
- Usage guide and clip updated

#### Shift holds a drag level until it strays far across

- Held on the line it mostly runs along, so small nudges stay level; a big stray moves freely
- Snaps only along the held line; Shift pressed or let go mid-drag applies right away
- A Shift-press on a selected layer drags the selection; a Shift-click drops the layer

#### A selected layer shows dashed lines to its frame's edges

- Like Figma: from the frame's left and top edges to the layer, through its middle
- Only for one selected layer inside a frame that places children freely
- Hidden while measuring or editing points or a crop

#### A click anywhere on an empty Fill, Stroke or Effects row adds one

- As in Figma; the + still works, and rows that already have entries ignore the click
- Verify-section-add checks each row in the app

#### A marquee from the canvas selects inside artboards it only partly covers

- Like Figma: the layers it touches inside the artboard, not the artboard; the artboard only when fully covered
- Frames holding artboards pass through the same way

#### Present and PDF export play only artboards

- An artboard is one slide or page, never split into its cards
- A frame holding artboards plays them under its title, never itself
- Export drops the option to split section frames into pages

#### Drop a layer on a frame to move it inside

- Dragging on the canvas lands layers in the frame under the pointer, outlined while you drag
- Dragged off their frame onto empty canvas, they go to the top level
- An artboard dropped into another becomes a plain frame there
- Verify-artboards drags a frame into an artboard and back out

#### A frame dropped into an artboard becomes a plain frame

- Moving into an artboard clears its Artboard setting and any inside it
- Moving into a plain holder keeps it an artboard

#### An Artboards clip for the guide and its info card

- Miles shows turning on Use as artboard for a frame inside another

#### Drop the size menu from the Artboard section

- Artboard section is the toggle and its note, no size presets
- Artboard tool still places 1440 x 1024

#### An Artboard tool, panel section and menu rows

- Artboard tool (B) in the toolbar, white fill, Desktop size on click
- Right panel Artboard section: on/off and size presets
- Frames drawn inside an artboard start with no fill
- Layers shows artboards with the corner marks icon
- Right-click Flatten, Make artboard / Make plain frame
- Export, Present and Share pick from artboards

#### Agents mark artboards and keep the tree shallow

- Flatten(id) removes wrappers that draw nothing, on request
- ctx.problems flags a redundant wrapper the call just made
- Warning when an artboard is marked inside another one
- Skill: depth budget artboard › section › row › element, no groups
- Brainstorm holders are plain frames; screens inside are artboards

#### Clicks and labels follow artboards at any depth

- Clicks pass through plain holders to the artboard inside
- Artboards inside a holder get their own name label
- Marquee starts inside the artboard under the pointer

#### Flatten removes wrappers that do nothing

- A wrapper is a frame or group with one child filling it exactly and nothing drawn
- Flatten removes them innermost first and keeps the look; artboards and components stay

#### Any frame can be an artboard

- Frames take artboard: true to be one anywhere, false to make a top-level frame a plain holder
- Top-level frames stay artboards by default; holding a marked frame makes them a holder
- Artboards don't nest: the outer one wins
- Present and PDF give a holder one page per artboard inside it

#### A component edit relays out and repaints only its instances

- Layout keeps nodes whose change only affects paint, like a component's fill
- A component edit marks just its instances and the frames above them as changed
- perf-component-edit.ts times a component edit across hundreds of instances

#### Pasted instances keep their copied component

- Instances pasted with their component on another board stayed empty: the paste dropped the new ids they pointed at
- Verify-paste-instances copies a component and its instances to a new board

## 0.2.22 (2026-10-30)

#### See the whole team's usage, and numbers stay current

- Signed in to an organization that keeps usage, Usage opens on everyone's, boards you never joined included; a picker narrows it to this computer
- Each device sends its own usage to the organization a minute after start and after runs
- Opening Usage catches closed boards up with the relay first, so teammates' recent runs show
- Token counts read in billions and trillions (1.1B, not 1120.9M)
- Claude Code terminal work that used Autopen always counts; the switch for it is gone
- Closing a board no longer risks saving older usage numbers over newer ones

## 0.2.21 (2026-10-30)

#### Share links get a tab icon and the app's zoom keys

- The tab shows the app's icon, another app's from its own icon set
- ⌘/Ctrl + and − zoom, Shift+0 is 100%, Shift+1 fits

#### Duplicate a listed board you haven't joined

- Duplicate… shows on every board's right-click menu
- A board not yet on this computer is joined first, and the copy waits for its contents

#### Double-click a sticky note to edit it in place

- The note opens as it looks: bold stays bold, bullets stay bullets
- A bar above it does bold, italic, headings, bullets and numbers; ⌘B and ⌘I work
- Typing "- ", "1. " or "# " starts a list or heading
- Enter on a selected note opens it too; the note grows when its text outgrows it

#### The left sidebar folds to its rail

- A button at the bottom of the rail folds the sidebar to its icons and opens it again
- Any tab opens it back up; clicking the open tab folds it
- It stays folded across boards and restarts; ⌘\ still hides everything
- Help clips and the welcome film show the new button

#### Glass backdrops record instead of rasterizing on the CPU

- A backdrop is recorded as a picture shader, so the surface drawing it rasterizes it on the GPU
- A board of glass tiles over a noise shader no longer reruns that shader on the CPU per tile

## 0.2.20 (2026-10-29)

#### The usage card says how old its numbers are

- "Updated just now" or "Updated 6m ago" under the limits

#### People away from the board drop off its avatars

- Presence carries an away flag; avatars show others only while the board is their open, focused tab

#### Present always opens its setup

- With nothing selected it opens on Whole board; Selection is disabled until frames are selected
- Enter plays; Mod+Alt+Enter still plays at once

#### A setup popover for the selection

- order, tall pages, copy link

#### New Features

- One toast system, clear of the canvas toolbar
- Toasts on the canvas, and rows open their conversation
- Agents strip, inbox popover and tab dots
- Main keeps every board's agent runs for this device
- Settle a conversation from the header, the list and its menu
- Settled state and folded sub-agents in the thread model
- Settled conversations, per board in the doc
- The usage chip shows the 5-hour limit
- Usage chip and model gauge by Send
- View can show the frames selected on the canvas
- Shared links heads its scoped section Frame and layer links
- Links to selected frames, kept live in their saved slide order
- A frames scope for links, carrying the saved slide order
- A slide order saved on the board per set of frames
- Hide the bar (H) and fit tall pages to the width
- Present the selected frames
- Share is Edit and View, with a bar saying what each link needs

#### The app stays smooth while agents bulk edit

- Shadows under an opaque fill draw without a cut-out, so redrawing a page of shadowed cards no longer stalls a frame for 100-200ms
- Canvas tiles flush as they render, so the per-frame budget counts the GPU work and a big edit repaints over a few frames
- Agent layout keeps unchanged trees and Yoga nodes between calls, so growing a big frame no longer holds the main process (and every key and click) each edit
- bench-composer: typing latency, frame pacing and main-process stalls while an agent edits

#### Opening a listed board you haven't joined joins it first

- Picking it from the new-tab palette joins from the stored invite, then opens it
- A join that fails says why on Home

#### One-layer links draw layers holding instances of deleted components

- A View link to a screen with leftover copies of a deleted component showed "This layer is no longer on the board".
- Those leftovers are left out of the link, the way the board already leaves them out.

## 0.2.19 (2026-10-29)

#### Menu button on Windows and Linux

- A menu button at the left of the tab strip opens the app menu, which the hidden title bar leaves out

#### Present the board as slides in the app

- Present in the top bar plays the board as slides right in the window, starting on the selected slide.
- F goes full screen; Escape or the X brings you back to the canvas where you left it.
- Also starts from a frame's right-click menu, Option-Cmd-Enter, View > Present, or a narrated deck's slide strip.
- The browser Present link and the app share one slideshow.

#### Format tiles are all the same width

- Each group in the export dialog grows by its tile count, so every format tile matches

#### Dropped HTML files import the way the browser shows them

- Bundled exports that build their page in frames import whole, every section included
- Pills, buttons and labels inside frames stay where the page puts them
- Dropdowns show their chosen value and arrow; checkboxes and radios come along
- Input text aligns and clips like the page; textarea text starts at the top and wraps
- Fieldset borders break behind their legend
- Dashed and dotted borders stay dashed and dotted
- Pages wider than the window import at their full width

#### PDFs and SVGs match the board for logos, screenshots and borders

- Image fills with pen.dev's modes ("fit", "fill") export as contain and cover, as the canvas draws them, instead of at full size.
- Agents get a warning when they write those modes or a stroke as { fill, thickness }.
- SVG image fills on shapes are clipped images, not patterns, so PDFs keep them sharp.
- One-sided strokes and drop shadows in SVGs are vector clips, not masks.
- SVG ids are unique per export, so several SVGs on one page don't swap images.
- Double spaces in SVG text hold when the SVG sits in a web page.

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
