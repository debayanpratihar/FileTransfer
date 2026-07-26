from pathlib import Path

md = r"""# 04_CANVAS_ENGINE.md

# AI Notebook - Canvas Engine Specification

Version: 1.0

> This document defines the complete canvas engine. The canvas is the heart of the application. Every notebook interaction must be built around this specification.

---

# Vision

The canvas should feel like writing on premium paper while providing infinite digital flexibility.

The user should never think about pages, rendering, memory, or limits.

Everything should feel instant.

---

# Core Requirements

- Infinite canvas in all directions
- Hardware accelerated rendering
- Smooth drawing
- Smooth scrolling
- Smooth zooming
- 60 FPS minimum
- Target 120 FPS on supported devices
- Zero visible redraw flicker
- Autosave while drawing

---

# Rendering Architecture

Use a tile-based renderer.

Requirements:

- Divide canvas into fixed-size tiles.
- Render only visible tiles.
- Keep nearby tiles in memory.
- Unload distant tiles automatically.
- Background tile generation.
- Dirty-tile redraw instead of full canvas redraw.

The renderer must never redraw the entire notebook after a single stroke.

---

# Coordinate System

Maintain a world coordinate system independent of screen size.

Requirements:

- Floating-point coordinates
- Device-independent rendering
- Rotation-safe
- Zoom-safe
- Pan-safe

Never store strokes in screen coordinates.

---

# Stroke Model

Every stroke stores:

- Unique ID
- Tool type
- Color
- Width
- Opacity
- Pressure samples
- Timestamp
- Point list
- Bounding box

Strokes must remain editable.

---

# Stroke Smoothing

Goals:

- Preserve the user's handwriting style.
- Remove jitter.
- Low latency.

Preferred techniques:

- Bézier interpolation
- Catmull-Rom splines
- Velocity-based smoothing

Allow users to adjust smoothing strength.

---

# Stylus Support

Support:

- Pressure sensitivity
- Palm rejection
- Tilt (future)
- Hover (where available)
- Button shortcuts

Finger and stylus events should be handled independently.

---

# Multi-touch Gestures

Support:

- Single finger draw
- Two finger pan
- Pinch zoom
- Double tap zoom
- Long press selection

Drawing must never stop while another finger pans the canvas.

---

# Zoom

Minimum: 10%

Maximum: 1000%

Maintain crisp vector rendering at every zoom level.

Never rasterize strokes permanently.

---

# Layers

Support multiple layers.

Each layer supports:

- Rename
- Lock
- Hide
- Duplicate
- Reorder
- Delete
- Merge

Future support:

- Blend modes
- Opacity

---

# Selection

Provide:

- Rectangle selection
- Lasso selection

Selected objects support:

- Move
- Rotate
- Resize
- Duplicate
- Delete
- Group

---

# Shapes

Support:

- Line
- Arrow
- Rectangle
- Rounded Rectangle
- Circle
- Ellipse
- Triangle
- Polygon
- Star
- Cloud
- Speech Bubble

Optional smart recognition converts rough sketches into clean geometry.

---

# Templates

Templates should be rendered independently from strokes.

Supported templates:

- Blank
- Ruled
- Dot Grid
- Graph
- Engineering
- Music Staff
- Dark Variants
- Custom

Changing templates must not modify existing strokes.

---

# Undo / Redo

Requirements:

- Unlimited while memory permits
- Command-based history
- Fast replay
- Preserve AI-generated strokes separately from user strokes

---

# Autosave

Autosave continuously.

Requirements:

- Never interrupt drawing
- Save only modified tiles
- Crash-safe recovery
- Restore last session automatically

---

# Performance Targets

Drawing latency: <16 ms

Zoom latency: Smooth

Pan latency: Smooth

Memory usage: Adaptive

No UI freeze during redraw.

---

# Future Expansion

The architecture must support:

- Infinite pages
- Collaborative editing
- Cloud sync
- Vector export
- Presentation mode
- Whiteboard mode

---

# Acceptance Criteria

The canvas is complete only if:

- It feels like writing on paper.
- Large notebooks remain responsive.
- AI writing and user writing coexist without conflicts.
- Rendering remains smooth during drawing, zooming, and panning.
"""

path = Path("/mnt/data/04_CANVAS_ENGINE.md")
path.write_text(md, encoding="utf-8")
print(path)
