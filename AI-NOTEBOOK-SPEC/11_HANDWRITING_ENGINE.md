

# AI Notebook - Handwriting Engine Specification

Version: 1.0

## Purpose

This document defines how handwriting is captured, processed, rendered, animated, recognized, and reproduced by both the user and the on-device AI.

The handwriting engine must preserve the natural feel of handwriting while allowing AI to write seamlessly alongside the user.

---

# Design Philosophy

The handwriting engine must:

- Preserve the user's natural handwriting.
- Never force handwriting normalization.
- Produce smooth and readable strokes.
- Make AI writing feel as if it were written in the same notebook.
- Operate completely offline.

---

# Handwriting Capture

Each pen stroke records:

- X coordinate
- Y coordinate
- Timestamp
- Pressure (if available)
- Stroke width
- Pen type
- Color
- Opacity

Capture data continuously until stroke completion.

---

# Handwriting Processing Pipeline

Raw Touch Events

↓

Point Sampling

↓

Noise Reduction

↓

Stroke Smoothing

↓

Bezier/Spline Generation

↓

Vector Stroke Creation

↓

Canvas Rendering

↓

Autosave

---

# Stroke Smoothing

Objectives:

- Remove unwanted jitter
- Maintain original writing style
- Minimize latency

Smoothing Modes:

- Disabled
- Low
- Medium
- High
- Adaptive

Adaptive mode automatically adjusts smoothing based on writing speed.

---

# Handwriting Profiles

Users may select:

- Natural
- Neat
- Printed
- Technical Notes
- Cursive
- Minimal

Profiles only affect AI-generated handwriting unless explicitly applied to user writing.

---

# AI Handwriting

The AI must write using the same vector stroke engine as the user.

Requirements:

- Stroke-by-stroke generation
- Natural writing animation
- Editable strokes
- Undo/Redo support
- Consistent spacing
- Consistent margins

The AI must never insert bitmap text into the notebook.

---

# AI Writing Placement

Priority:

1. Right side of the user's notes
2. Below existing notes
3. New continuation region

Rules:

- Never overwrite user handwriting.
- Avoid overlapping drawings.
- Expand the canvas automatically if needed.

---

# Writing Animation

AI handwriting should appear progressively.

Animation stages:

1. Think
2. Begin writing
3. Draw each stroke
4. Pause naturally between words
5. Finish

Users may:

- Disable animation
- Increase animation speed
- Instantly render completed handwriting

---

# OCR Integration

Use on-device ML Kit.

Support recognition of:

- Printed English
- Handwritten English
- Mixed notes

OCR is used for:

- Search
- AI context
- Indexing
- Export

Original handwriting must never be modified after OCR.

---

# Mathematical Notation

Support clear handwritten rendering of:

- Fractions
- Integrals
- Matrices
- Summations
- Greek symbols
- Superscripts
- Subscripts

AI should preserve notebook formatting when writing mathematical expressions.

---

# Handwriting Customization

Users can configure:

- Stroke smoothing
- Pen pressure
- Default ink color
- Writing animation speed
- AI handwriting style
- AI ink color

Changes apply to future strokes only.

---

# Storage Format

Each handwritten stroke stores:

- UUID
- Tool
- Color
- Width
- Opacity
- Point list
- Pressure values
- Timestamp
- Bounding box

Data remains editable at all times.

---

# Performance Targets

- Handwriting latency under 16 ms
- Smooth animation at 60 FPS
- OCR processing on-device
- No UI blocking during AI writing
- Adaptive memory usage

---

# Privacy

All handwriting remains on-device.

No handwriting data is uploaded except when the user explicitly exports or shares content.

---

# Acceptance Criteria

The handwriting engine is complete only if:

- User handwriting remains natural.
- AI handwriting blends seamlessly into the notebook.
- OCR does not alter original notes.
- AI writing never overwrites user content.
- Handwriting remains editable after saving and reopening notebooks.
"""

