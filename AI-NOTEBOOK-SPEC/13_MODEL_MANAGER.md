from pathlib import Path

content = r"""# 08_MODEL_MANAGER.md

# AI Notebook - Model Manager Specification

Version: 1.0

## Purpose

The Model Manager is responsible for discovering, downloading, validating, installing, updating, selecting, and removing AI models used by the application. It provides a safe and reliable lifecycle for local GGUF models while remaining completely transparent to the user.

---

# Design Goals

The Model Manager must:

- Be simple to use.
- Support offline inference.
- Download models only from trusted sources.
- Detect device compatibility automatically.
- Prevent installation of unsupported models.
- Recover safely from interruptions.

---

# Supported Model Format

Initial supported format:

- GGUF

Inference backend:

- llama.cpp

Future formats may be added without changing the user interface.

---

# Configuration Source

Configuration is read from:

https://debayanpratihar.github.io/ai-notebook-config/

Required files:

- config.json
- models.json
- announcements.json
- changelog.json

The configuration service defines:

- Available models
- Recommended models
- Minimum app version
- Download URLs
- SHA-256 hashes
- Release notes

---

# Trusted Download Sources

Default source:

- Hugging Face

Requirements:

- HTTPS only
- Resume support
- Background downloads
- Download verification

Downloads from unknown sources should require explicit user confirmation.

---

# Device Compatibility Check

Before download, inspect:

- Android version
- CPU ABI
- Available RAM
- Free storage
- CPU architecture
- Available threads

Recommend the most suitable model automatically.

---

# Recommended Models

Compact

- Qwen2.5 1.5B Instruct (Q4_K_M)

Balanced

- Qwen2.5 3B Instruct (Q4_K_M)

High Quality

- Qwen2.5 7B Instruct (Q4_K_M)

The recommendation engine may evolve without requiring an application update.

---

# Model Metadata

Each installed model stores:

- Unique ID
- Display name
- Version
- Provider
- File size
- SHA-256
- Download URL
- Local path
- Install date
- Last used
- Compatible devices
- Minimum RAM
- Recommended RAM

---

# Download Workflow

Discover Model

↓

Compatibility Check

↓

Start Download

↓

Pause / Resume

↓

Integrity Verification

↓

Installation

↓

Ready for Use

---

# Download Features

Support:

- Start
- Pause
- Resume
- Cancel
- Retry
- Background download
- Progress percentage
- Remaining time estimate
- Download speed

Interrupted downloads should resume automatically when possible.

---

# Integrity Verification

After download:

- Calculate SHA-256 hash.
- Compare with configuration.
- Reject corrupted files.
- Prompt user to retry if verification fails.

Models failing verification must never be loaded.

---

# Installation

Requirements:

- Atomic installation
- Rollback on failure
- Verify storage space
- Register model metadata
- Mark active version

Installation must not block the UI.

---

# Model Selection

Users may:

- Activate model
- Deactivate model
- Switch model
- View model information
- Delete model

Only one model is active by default.

---

# Update Strategy

Check configuration periodically.

If a newer compatible model exists:

- Notify user
- Show release notes
- Allow update
- Keep current model until update succeeds

Automatic updates remain optional.

---

# Storage Management

Display:

- Installed models
- Total storage used
- Individual model sizes
- Free device storage

Allow users to remove unused models.

---

# Error Handling

Gracefully handle:

- Network interruption
- Low storage
- Insufficient RAM
- Corrupted download
- Missing configuration
- Unsupported device

Always provide a recovery option.

---

# Security

Requirements:

- HTTPS downloads only
- SHA-256 verification
- Validate metadata
- Reject incomplete models

Never execute unverified model files.

---

# Future Expansion

Architecture should support:

- Multiple providers
- Quantization variants
- Delta updates
- Parallel downloads
- Vision-language models
- Audio models
- Plugin model repositories

---

# Acceptance Criteria

The Model Manager is complete only if:

- Compatible models are recommended automatically.
- Downloads can pause and resume safely.
- Corrupted models are rejected.
- Installed models remain selectable without restarting the app.
- Model updates never interrupt notebook usage.
"""

path = Path("/mnt/data/08_MODEL_MANAGER.md")
path.write_text(content, encoding="utf-8")
print(path)
