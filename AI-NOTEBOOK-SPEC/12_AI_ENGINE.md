from pathlib import Path

content = r"""# 07_AI_ENGINE.md

# AI Notebook - Offline AI Engine Specification

Version: 1.0

## Purpose

This document specifies the complete Offline AI Engine for AI Notebook. The AI must operate entirely on-device using GGUF language models executed through llama.cpp, integrating naturally into the notebook instead of a traditional chat interface.

---

# Design Philosophy

The AI should behave like an intelligent study partner.

Principles:

- Offline-first
- Privacy-first
- Notebook-first
- Low latency
- Interruptible generation
- Editable AI output
- Modular architecture

The AI must never replace the notebook experience.

---

# Architecture Overview

Components:

- AI Manager
- Model Manager
- Prompt Builder
- Context Extractor
- Inference Engine
- Token Stream Manager
- Handwriting Generator
- Response Formatter
- Memory Manager
- Download Manager

Each component should be independently testable.

---

# AI Workflow

User Action

↓

Context Extraction

↓

Prompt Construction

↓

Model Selection

↓

Token Generation

↓

Response Formatting

↓

Handwriting Rendering

↓

Notebook Update

---

# Local Model Execution

Requirements:

- Use llama.cpp
- Support GGUF models
- CPU inference
- Optional GPU acceleration when supported
- Dynamic thread allocation
- Streaming token generation

No internet connection is required after model installation.

---

# Supported Models

Initial recommendations:

- Qwen2.5 1.5B Instruct (Q4_K_M)
- Qwen2.5 3B Instruct (Q4_K_M)
- Qwen2.5 7B Instruct (Q4_K_M)

Future models should be installable through configuration updates.

---

# Configuration

Read configuration from:

https://debayanpratihar.github.io/ai-notebook-config/

Files:

- config.json
- models.json
- announcements.json
- changelog.json

Configuration updates must not require an application update.

---

# Prompt Builder

The Prompt Builder constructs prompts using:

- User handwriting
- OCR text
- Nearby drawings
- Previous AI responses
- Notebook metadata
- User settings

Prompt construction must remain internal and invisible to users.

---

# Context Extraction

Gather relevant information from:

- Current viewport
- Current notebook
- Selected region
- OCR results
- Imported PDFs
- Images (future)

Only include information necessary for the current task.

---

# AI Generation Modes

Support:

- Automatic
- Manual
- Continue
- Regenerate
- Stop

Users may disable automatic generation globally.

---

# Token Streaming

Requirements:

- Stream tokens continuously.
- Convert tokens into formatted notebook content.
- Begin handwriting before full completion when appropriate.
- Allow interruption without corrupting notebook data.

---

# Handwriting Output

The AI must:

- Use vector strokes
- Follow notebook margins
- Respect selected handwriting style
- Animate writing naturally
- Produce editable content

Never insert bitmap handwriting.

---

# Memory Management

Requirements:

- Load only one active model by default
- Release unused memory automatically
- Prevent OutOfMemory crashes
- Warn users before loading unsupported models

---

# Download Manager

Support:

- Download
- Pause
- Resume
- Retry
- Delete
- SHA-256 verification
- Progress display
- Background downloads

---

# Performance Targets

Cold model load:
< 10 seconds (device dependent)

Token generation:
Responsive on supported hardware

UI:
Never block drawing or navigation during inference.

---

# Privacy

All inference is performed locally.

No notebook content, prompts, OCR data, or generated responses are uploaded unless explicitly exported by the user.

---

# Error Handling

Handle gracefully:

- Missing model
- Corrupted model
- Low storage
- Low RAM
- Interrupted generation
- Configuration download failure

Provide clear recovery actions.

---

# Future Expansion

Architecture should support:

- Vision-language models
- Speech recognition
- Speech synthesis
- Multi-model routing
- Agent workflows
- Cloud synchronization (optional)
- Plugin architecture

---

# Acceptance Criteria

The AI Engine is complete only if:

- All supported models run locally.
- AI generation never blocks notebook interaction.
- Responses are rendered directly into the notebook.
- Users can interrupt generation at any time.
- All generated handwriting remains editable.
"""

path = Path("/mnt/data/07_AI_ENGINE.md")
path.write_text(content, encoding="utf-8")
print(path)
