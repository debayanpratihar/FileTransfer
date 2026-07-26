

# AI Notebook UI / UX Specification

Version: 1.0

## Purpose

This document defines every major screen, navigation pattern, toolbar, interaction, animation, and UX principle for AI Notebook.

Claude Code must follow this document when implementing UI.

---

# Design Principles

- Minimal distractions
- Notebook is always the primary focus
- AI feels like a writing partner, not a chatbot
- One-handed operation where possible
- Material 3 with custom notebook styling
- Fluid animations (60 FPS minimum)

---

# Navigation Structure

Home
├── Recent Notebooks
├── All Notebooks
├── Favorites
├── Trash
├── Settings
└── Model Manager

Notebook
├── Infinite Canvas
├── Toolbar
├── AI Controls
├── Layers
├── Templates
└── Export

---

# Home Screen

Sections:
- Search bar
- Recent notebooks
- Folder grid
- Create notebook button
- Import PDF
- Import Image
- Quick AI status
- Installed model indicator

Floating Action Button:
+ New Notebook

---

# Notebook Screen

The notebook occupies almost the entire screen.

Top App Bar:
- Back
- Notebook name
- Save status
- Search
- More menu

Bottom Toolbar:
- Pen
- Pencil
- Highlighter
- Marker
- Eraser
- Lasso
- Shapes
- Text
- Image
- AI
- Undo
- Redo

Toolbar should be scrollable on small devices.

---

# Canvas Interaction

Gestures:
- Single finger draw
- Two finger pan
- Pinch zoom
- Double tap zoom
- Long press selection
- Stylus priority over finger

Zoom:
Minimum: 10%
Maximum: 1000%

Display current zoom percentage.

---

# Color Picker

Provide:
- Preset colors
- Custom RGB
- HEX input
- Recent colors
- Favorite colors
- Opacity slider

---

# Stroke Settings

Each drawing tool supports:
- Width
- Opacity
- Pressure curve
- Smoothing
- Stabilization

---

# Shape Tool

Supported:
- Line
- Arrow
- Rectangle
- Circle
- Ellipse
- Triangle
- Polygon
- Star
- Cloud
- Speech Bubble

Optional smart recognition toggle.

---

# Grid Selector

Templates:
- Blank
- Ruled
- College
- Dot
- Square
- Graph
- Engineering
- Music Staff
- Dark
- Custom

Allow changing template without affecting drawings.

---

# AI Panel

The AI panel is NOT a chat.

Controls:
- Generate
- Stop
- Continue
- Regenerate

Options:
- Automatic AI
- Manual AI
- AI handwriting style
- Ink color
- Animation speed

Status:
- Ready
- Thinking
- Writing
- Stopped

---

# Model Manager Screen

Display:
- Installed model
- Recommended model
- Download progress
- RAM requirement
- Storage requirement
- Delete model
- Verify model

Configuration source:

https://debayanpratihar.github.io/ai-notebook-config/

Read:
- config.json
- models.json
- announcements.json
- changelog.json

---

# Settings

Sections:
- Appearance
- AI
- Canvas
- Handwriting
- Downloads
- Storage
- Accessibility
- About

---

# Dark Mode

All notebook templates must have dark variants.

Ink colors should automatically adapt for visibility.

---

# Accessibility

- Large touch targets
- Screen reader labels
- High contrast mode
- Stylus friendly
- Left-handed mode

---

# Acceptance Criteria

The UI is complete only if:

- All actions are discoverable.
- Drawing never feels delayed.
- AI never blocks user interaction.
- The notebook remains the center of the experience.
"""
