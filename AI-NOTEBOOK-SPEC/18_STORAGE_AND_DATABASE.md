# 09_NOTEBOOK_STORAGE.md

# AI Notebook - Notebook Storage Specification

Version: 1.0

## Purpose

This document defines how notebooks, pages, strokes, AI annotations, metadata, templates, and application data are stored locally. The storage layer must be reliable, scalable, crash-safe, and optimized for large notebooks.

---

# Design Principles

- Offline-first
- Fast loading
- Crash recovery
- Versioned data
- Incremental saving
- Minimal storage usage
- Future cloud-sync ready

---

# Storage Architecture

Components:

- Room Database
- Local File Storage
- Tile Cache
- Model Storage
- Export Manager
- Backup Manager
- DataStore (preferences)

Each component must have clear ownership and lifecycle.

---

# Suggested Directory Structure

Android/data/<package>/

├── notebooks/

├── exports/

├── imports/

├── cache/

├── models/

├── thumbnails/

├── backups/

└── logs/

The application should automatically create missing directories.

---

# Room Database

Primary entities:

- Notebook
- Folder
- Page
- Stroke
- Layer
- AIAnnotation
- Template
- Tag
- Attachment

Relationships must support efficient querying.

---

# Notebook Metadata

Each notebook stores:

- UUID
- Name
- Description
- Created date
- Modified date
- Thumbnail
- Template
- Tags
- Folder
- Color
- Archived status
- Favorite status

---

# Page Metadata

Each page stores:

- UUID
- Notebook ID
- Canvas size
- Background template
- Zoom state
- Layer count
- Creation time
- Last edited

---

# Stroke Storage

Each stroke contains:

- UUID
- Page ID
- Layer ID
- Tool
- Color
- Width
- Opacity
- Pressure samples
- Point list
- Bounding box
- Timestamp

Strokes remain editable.

---

# AI Annotations

Store separately from user strokes.

Fields:

- UUID
- Related page
- Related prompt
- Generated time
- Model used
- Placement region
- Editable state

AI annotations participate in undo/redo.

---

# Autosave

Requirements:

- Save modified content only
- Trigger during idle periods
- Never interrupt drawing
- Maintain recovery checkpoints

If the application closes unexpectedly, the latest checkpoint should be restored.

---

# Cache

Cache may contain:

- Rendered tiles
- OCR index
- Temporary exports
- Image previews
- PDF previews

The cache must be safely removable.

---

# Export Formats

Support:

- PDF
- PNG
- JPEG
- Native notebook package

Future:

- SVG
- Markdown
- HTML

---

# Import Formats

Support:

- PDF
- Images
- Native notebook package

Future:

- OneNote
- GoodNotes
- Markdown

---

# Backup

Provide:

- Manual backup
- Automatic backup
- Restore
- Backup validation

Backups should preserve notebook metadata and AI annotations.

---

# Data Versioning

Every notebook contains:

- File format version
- Application version
- Schema version

Migration logic must support opening notebooks created by earlier versions.

---

# Security

Requirements:

- Private app storage by default
- Validate imported files
- Protect against corrupted notebook packages
- Prepare for optional encryption in future releases

---

# Performance Targets

- Open recent notebook quickly
- Save incrementally
- Handle thousands of strokes
- Avoid unnecessary database writes

---

# Error Handling

Gracefully recover from:

- Corrupted notebook
- Missing assets
- Low storage
- Failed export
- Failed import
- Interrupted save

Never lose confirmed user edits.

---

# Future Expansion

Architecture should support:

- Cloud synchronization
- Collaboration
- End-to-end encryption
- Version history
- Notebook sharing
- External storage providers

---

# Acceptance Criteria

The storage layer is complete only if:

- User data survives unexpected shutdowns.
- Autosave is transparent.
- Large notebooks remain responsive.
- Import and export preserve notebook fidelity.
- Data schema supports future expansion without breaking compatibility.
