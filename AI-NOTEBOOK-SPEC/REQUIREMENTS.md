# 02_REQUIREMENTS.md

# AI Notebook - Software Requirements Specification (Part 1)

Version: 1.0

This document defines the functional and non-functional requirements for the AI Notebook Android application.

Configuration URL:
https://debayanpratihar.github.io/ai-notebook-config/

The application must consume:
- config.json
- models.json
- announcements.json
- changelog.json

Models are downloaded from Hugging Face and executed locally using llama.cpp.

---

## Product Goal

Build a production-quality offline AI notebook where AI writes directly inside the notebook instead of a chat interface.

---

## Functional Requirements

### Infinite Canvas

- Infinite vertical and horizontal scrolling
- Smooth panning
- Pinch zoom
- Double tap zoom
- Zoom percentage
- Minimap
- Undo / Redo
- Tile-based rendering
- Minimum 60 FPS

### Drawing Tools

Provide:
- Pen
- Fountain Pen
- Pencil
- Marker
- Highlighter
- Brush
- Calligraphy Pen
- Eraser
- Stroke Eraser
- Object Eraser
- Lasso
- Shape Tool
- Text Tool
- Image Tool

Each tool supports:
- Color
- Width
- Opacity
- Pressure sensitivity
- Stroke smoothing
- Favorite presets

### Shapes

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

Optional smart shape recognition.

### Canvas Templates

Support:
- Blank
- Ruled
- College Ruled
- Wide Ruled
- Dot Grid
- Square Grid
- Graph Paper
- Engineering Grid
- Music Staff
- Dark Templates
- Custom Templates

### AI

AI writes directly onto the notebook.

Modes:
- Automatic
- Manual Generate
- Stop Generation
- Regenerate
- Continue Answer

Placement:
1. Right side
2. Below
3. Continuation area

Never overwrite user content.

### OCR

Use ML Kit.

Recognize:
- Handwriting
- Printed text

Never modify original handwriting.

### Notebook Management

Support:
- Create
- Rename
- Duplicate
- Archive
- Delete
- Export PDF
- Import PDF
- Export notebook
- Import notebook

### Model Manager

Recommend models based on:
- RAM
- Storage
- CPU
- Android Version

Support:
- Download
- Pause
- Resume
- Delete
- SHA256 Verification
- Background Download

### Settings

Provide settings for:
- Appearance
- AI
- Canvas
- Drawing
- Downloads
- Storage
- Accessibility
- Diagnostics

---

## Non Functional Requirements

- Offline First
- Compose Only
- Kotlin
- Material 3
- Clean Architecture
- MVVM
- Hilt
- Room
- DataStore
- Coroutines
- Flow
- WorkManager
- OkHttp
- ML Kit
- llama.cpp

Performance Targets:
- Drawing latency under 16ms
- Smooth 60 FPS rendering
- No UI freezes during AI inference

---

## Acceptance Criteria

The implementation is complete only if:
- AI never blocks drawing.
- User data remains on-device.
- Features follow this specification.
- No placeholder implementations exist.
