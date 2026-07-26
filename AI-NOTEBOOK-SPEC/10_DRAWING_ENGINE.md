from pathlib import Path

content = r"""# 05_DRAWING_ENGINE.md

# AI Notebook - Drawing Engine Specification

Version: 1.0

## Purpose

This document specifies the complete drawing engine for AI Notebook. The goal is to deliver a writing experience comparable to premium note-taking applications while remaining fully vector based and optimized for local AI integration.

---

# Design Goals

The drawing engine must:

- Feel like writing on real paper.
- Preserve the user's handwriting style.
- Maintain extremely low latency.
- Scale to very large notebooks.
- Support stylus and finger input.
- Remain fully editable.

---

# Supported Tools

## Writing

- Ball Pen
- Fountain Pen
- Pencil
- Mechanical Pencil
- Marker
- Brush
- Calligraphy Pen
- Highlighter

## Editing

- Stroke Eraser
- Object Eraser
- Pixel Eraser (future)
- Lasso
- Selection
- Shape Tool

---

# Brush Properties

Each tool exposes:

- Color
- Width
- Opacity
- Pressure sensitivity
- Smoothing
- Stabilization
- Minimum width
- Maximum width
- Favorite presets

Changes should preview in real time.

---

# Stroke Pipeline

Input Event

↓

Point Sampling

↓

Pressure Sampling

↓

Smoothing

↓

Bezier / Spline Generation

↓

Vector Stroke Generation

↓

GPU Rendering

↓

Autosave

---

# Stroke Sampling

Capture:

- X coordinate
- Y coordinate
- Timestamp
- Pressure
- Tool type

Discard duplicate points.

---

# Smoothing

Primary objective:

Reduce hand jitter without changing writing style.

Support:

- Off
- Low
- Medium
- High
- Adaptive

Adaptive mode should increase smoothing at low drawing speeds.

---

# Fountain Pen

Characteristics:

- Variable stroke width
- Pressure sensitive
- Smooth curves
- Elegant joins

---

# Pencil

Characteristics:

- Slight texture
- Pressure variation
- Soft edges
- Natural appearance

---

# Marker

Characteristics:

- Thick stroke
- Uniform width
- Slight transparency

---

# Highlighter

Characteristics:

- Semi-transparent
- Multiply blend mode
- Text remains visible beneath

---

# Eraser

Support:

## Stroke Eraser

Deletes complete stroke.

## Object Eraser

Deletes selected object.

Future:

Pixel-level erasing.

---

# Shape Recognition

When enabled:

Detect rough drawings and convert into:

- Rectangle
- Circle
- Ellipse
- Triangle
- Arrow
- Line
- Polygon

Provide Undo support.

---

# Pressure Sensitivity

Support stylus pressure where available.

Users may disable pressure response.

Provide adjustable pressure curves.

---

# Palm Rejection

Requirements:

- Ignore accidental palm touches.
- Prioritize stylus events.
- Continue drawing smoothly while palm rests on screen.

---

# Color System

Support:

- Preset palette
- RGB
- HEX
- Recent colors
- Favorites

Future:

Gradient strokes.

---

# Rendering

Render all strokes as vectors.

Never permanently rasterize notebook content.

Maintain crisp quality at every zoom level.

---

# Storage

Store every stroke independently.

Each stroke contains:

- UUID
- Tool
- Color
- Width
- Opacity
- Pressure samples
- Point list
- Timestamp
- Bounding box

---

# Performance Targets

- Drawing latency <16 ms
- No dropped frames during continuous writing
- Smooth rendering on mid-range Android devices
- Minimal battery usage

---

# AI Compatibility

AI-generated handwriting must use the same stroke engine.

AI strokes should:

- Behave like user strokes
- Be editable
- Support undo/redo
- Respect notebook color and style settings

---

# Acceptance Criteria

The drawing engine is complete only if:

- Writing feels natural.
- Stroke smoothing preserves handwriting identity.
- Zooming never reduces quality.
- AI and user strokes share the same rendering pipeline.
"""

path = Path("/mnt/data/05_DRAWING_ENGINE.md")
path.write_text(content, encoding="utf-8")
print(path)
