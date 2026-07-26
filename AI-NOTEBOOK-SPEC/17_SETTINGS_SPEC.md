

# AI Notebook - Settings & Preferences Specification

Version: 1.0

## Purpose

This document defines every configurable setting in AI Notebook. Settings must allow users to personalize the application without affecting notebook compatibility or data integrity.

---

# Design Principles

- Simple and discoverable
- Safe default values
- Immediate feedback where possible
- Offline-first
- Changes persist across sessions
- Synchronization-ready for future cloud support

---

# Settings Categories

1. Appearance
2. Notebook
3. Canvas
4. Drawing
5. Handwriting
6. AI
7. Models
8. Downloads
9. Storage
10. OCR & Search
11. Accessibility
12. Privacy
13. Backup & Restore
14. Diagnostics
15. About
16. Developer Options

---

# Appearance

Options:

- Theme
  - System
  - Light
  - Dark

- Accent Color
- Dynamic Color (Android supported devices)
- Font Scale
- Animation Speed
- Language (future multilingual support)

---

# Notebook

Default options:

- Default notebook template
- Default page template
- Auto-create first page
- Notebook sorting
  - Name
  - Recently edited
  - Date created
- Default export format

---

# Canvas

User-configurable:

- Default zoom
- Zoom limits
- Grid visibility
- Snap to grid
- Infinite canvas toggle
- Mini-map visibility
- Show rulers
- Show page boundaries (optional)

---

# Drawing

Settings:

- Default tool
- Default pen width
- Default colors
- Pressure sensitivity
- Palm rejection
- Stroke smoothing
- Stabilization level
- Double-tap stylus shortcut (future)

---

# Handwriting

Options:

- Writing profile
- AI handwriting profile
- Writing animation
- Animation speed
- Ink color
- AI ink color
- Handwriting smoothing strength

---

# AI

Controls:

- Enable AI
- Automatic AI generation
- Inactivity timeout
- Preferred model
- Maximum context length
- Continue responses automatically
- Stream responses
- Handwriting animation

---

# Models

Display:

- Active model
- Installed models
- Download location
- Model storage usage
- Compatibility information
- Update availability

Actions:

- Download
- Verify
- Delete
- Switch active model

---

# Downloads

Options:

- Wi-Fi only downloads
- Background downloads
- Parallel downloads (future)
- Retry failed downloads
- Download notifications

---

# Storage

Display:

- Notebook storage
- Cache usage
- Model storage
- Free space

Actions:

- Clear cache
- Export logs
- Optimize storage

---

# OCR & Search

Settings:

- Enable OCR
- Automatic indexing
- Search AI annotations
- Rebuild search index
- OCR processing frequency

---

# Accessibility

Provide:

- High contrast mode
- Larger touch targets
- Left-handed mode
- Reduced motion
- Screen reader labels
- Stylus-friendly UI

---

# Privacy

Controls:

- Offline mode indicator
- Export consent prompts
- Crash report permission
- Analytics (disabled by default)
- Clear local AI history

No notebook content leaves the device without explicit user action.

---

# Backup & Restore

Support:

- Manual backup
- Automatic backup (future)
- Restore notebook package
- Verify backup integrity

---

# Diagnostics

Display:

- App version
- Database version
- Canvas engine version
- Active AI model
- Device information
- Available RAM
- Storage usage

Export diagnostics for troubleshooting.

---

# About

Display:

- App version
- Build number
- Licenses
- Open-source acknowledgements
- Privacy policy
- Changelog

---

# Developer Options

Hidden by default.

Options:

- Show FPS
- Canvas debug overlay
- AI timing metrics
- Tile renderer visualization
- OCR debug output
- Force software rendering
- Test handwriting animation

---

# Persistence

Use Jetpack DataStore.

Requirements:

- Atomic writes
- Corruption recovery
- Default fallback values
- Version-aware migrations

---

# Acceptance Criteria

Settings are complete only if:

- All changes persist after restart.
- Defaults provide an excellent first-run experience.
- Invalid configurations are prevented.
- Settings never corrupt notebook data.
"""

