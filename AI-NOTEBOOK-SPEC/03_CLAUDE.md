

# AI Notebook - Claude Code Implementation Guide

Version: 1.0

## Purpose

This guide provides Claude Code with the implementation rules, coding standards, priorities, and execution order required to build AI Notebook from the specifications in this repository.

---

# Primary Instruction

Before writing or modifying any code:

- Read every specification document (00–21).
- Treat the specifications as the single source of truth.
- Do not implement features that contradict the documented architecture.
- Prefer maintainability over short-term shortcuts.

---

# Technology Stack

Implement using:

- Kotlin
- Jetpack Compose
- Material 3
- MVVM
- Clean Architecture
- Hilt
- Room
- DataStore
- WorkManager
- ML Kit
- llama.cpp
- GGUF models

Avoid introducing additional frameworks unless they provide a clear long-term benefit.

---

# Implementation Priorities

Phase 1
- Project setup
- Module structure
- Dependency injection
- Navigation
- Database

Phase 2
- Infinite canvas
- Drawing engine
- Handwriting engine
- Notebook storage

Phase 3
- OCR
- AI engine
- Model manager
- Settings

Phase 4
- Export / Import
- Performance optimization
- Security hardening
- Testing

Phase 5
- Play Store release preparation

---

# Coding Standards

- Follow Kotlin style guidelines.
- Use meaningful names.
- Keep functions focused.
- Avoid duplicated logic.
- Prefer immutable data.
- Document public APIs.
- Write unit tests for business logic.

---

# Architecture Rules

Presentation
- Compose UI
- ViewModels

Domain
- Use Cases
- Repository interfaces

Data
- Repository implementations
- Room
- DataStore
- AI services

Never allow UI to access the database directly.

---

# UI Rules

- Compose only
- Material 3
- Responsive layouts
- Accessible components
- Smooth animations
- Dark mode support

---

# AI Rules

- Offline inference only
- Stream generated text
- Render AI output as handwriting
- Never overwrite user notes
- Always support cancellation
- Release model memory after use when appropriate

---

# Performance Rules

- No blocking work on the UI thread.
- Use coroutines appropriately.
- Render only visible canvas regions.
- Use lazy loading where possible.
- Profile memory regularly.

---

# Security Rules

- Validate imported files.
- Verify downloaded model hashes.
- Use HTTPS for downloads.
- Keep notebook content local by default.
- Never log notebook content.

---

# Error Handling

Every feature should:

- Fail gracefully
- Show meaningful user feedback
- Preserve user data
- Recover where possible

Avoid application crashes caused by recoverable errors.

---

# Testing Expectations

Every completed feature should include:

- Unit tests
- Integration tests where applicable
- UI tests for major workflows
- Manual verification

Do not merge incomplete features without validation.

---

# Documentation

When implementing:

- Update documentation if behaviour changes.
- Keep README current.
- Record architectural decisions.
- Maintain changelog entries.

---

# Definition of Done

A task is complete only if:

- Code compiles.
- Tests pass.
- Lint passes.
- Documentation is updated.
- Performance impact is acceptable.
- No critical known defects remain.

---

# Implementation Checklist

- Project builds successfully
- Architecture followed
- UI matches specification
- AI features behave as documented
- Offline mode verified
- Security requirements satisfied
- Performance benchmarks reviewed
- Release checklist completed

---

# Acceptance Criteria

Implementation guidance is complete only if Claude Code can:

- Build the project from the specifications.
- Maintain architectural consistency.
- Produce production-ready code.
- Preserve privacy-first and offline-first principles.
- Deliver a maintainable, scalable Android application.
""")

