

# AI Notebook - Project Structure Specification

Version: 1.0

## Purpose

This document defines the complete project structure, module organization, package conventions, resource layout, and coding standards for AI Notebook. The goal is to ensure the codebase remains maintainable, scalable, and easy to navigate as the application grows.

---

# Design Principles

- Feature-first organization
- Clean Architecture
- Modular development
- Low coupling
- High cohesion
- Easy testing
- Scalable for future expansion

---

# Root Project Structure

```
AI-Notebook/
├── app/
├── core/
├── common/
├── data/
├── domain/
├── feature-home/
├── feature-notebook/
├── feature-canvas/
├── feature-drawing/
├── feature-ai/
├── feature-models/
├── feature-search/
├── feature-export/
├── feature-settings/
├── docs/
├── scripts/
├── gradle/
└── buildSrc/
```

---

# Module Responsibilities

## app

Application entry point.

Contains:

- Application class
- Navigation host
- Dependency graph
- Theme setup
- Startup initialization

---

## core

Shared infrastructure.

Examples:

- Logging
- Utilities
- Extensions
- Result wrappers
- Constants
- Coroutine dispatchers

---

## common

Reusable UI components.

Examples:

- Buttons
- Dialogs
- Toolbars
- Color picker
- Loading indicators
- Empty states

---

## domain

Contains:

- Business models
- Repository interfaces
- Use cases
- Validation rules

Must not depend on Android framework.

---

## data

Contains:

- Room
- DataStore
- Repository implementations
- File storage
- OCR
- AI runtime integration
- Model manager

---

## Feature Modules

Each feature contains:

```
feature-name/
├── presentation/
├── domain/
├── data/
└── di/
```

Presentation:

- Screens
- ViewModels
- UI State
- Events

Domain:

- Feature-specific use cases

Data:

- Repository implementations
- Data sources

DI:

- Hilt modules

---

# Package Naming

Use lowercase.

Examples:

```
com.debayan.ainotebook
com.debayan.ainotebook.feature.ai
com.debayan.ainotebook.feature.canvas
com.debayan.ainotebook.data.room
```

Avoid abbreviations unless widely accepted.

---

# Resource Organization

```
res/
├── drawable/
├── font/
├── layout/
├── mipmap/
├── values/
├── xml/
└── raw/
```

Compose-first development should minimize XML usage.

---

# Assets

Suggested directories:

```
assets/
├── templates/
├── handwriting/
├── icons/
└── configs/
```

---

# AI Models

Store downloaded models outside bundled assets.

Suggested location:

```
files/models/
```

Do not package large GGUF models inside the APK.

---

# Documentation

Maintain documentation under:

```
docs/
```

Include:

- Architecture
- Specifications
- Changelog
- API documentation
- Release notes

---

# Build Variants

Provide:

- Debug
- Release

Future:

- Benchmark
- Internal testing

---

# Dependency Management

Use:

- Gradle Version Catalog (libs.versions.toml)

Group dependencies by:

- AndroidX
- Compose
- Networking
- Database
- Testing
- AI
- OCR

---

# Coding Standards

Requirements:

- Kotlin official style
- Immutable data classes
- Descriptive names
- Small functions
- Single responsibility
- KDoc for public APIs

Avoid:

- God classes
- Deep inheritance
- Global mutable state

---

# Testing Structure

```
src/
├── main/
├── test/
└── androidTest/
```

Test:

- Use cases
- ViewModels
- Repositories
- Room database
- Compose UI
- AI integration (mocked)

---

# CI/CD Readiness

Project should support:

- Static analysis
- Unit tests
- UI tests
- Lint
- Formatting
- Release builds

Future integration with GitHub Actions.

---

# Versioning

Follow Semantic Versioning:

MAJOR.MINOR.PATCH

Maintain changelog for every release.

---

# Acceptance Criteria

The project structure is complete only if:

- Features are isolated.
- Modules have clear responsibilities.
- Package names remain consistent.
- Shared code is reusable.
- The project scales cleanly without major restructuring.
"""

