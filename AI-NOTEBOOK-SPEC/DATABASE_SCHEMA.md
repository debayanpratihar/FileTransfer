

# AI Notebook - Database Schema Specification

Version: 1.0

## Purpose

This document defines the complete Room database schema for AI Notebook. The database stores notebook metadata, pages, strokes, AI annotations, templates, attachments, and search indexes while ensuring high performance, data integrity, and future extensibility.

---

# Design Principles

- Offline-first
- Normalized schema
- Fast queries
- Safe migrations
- Referential integrity
- Scalable relationships
- Backward compatibility

---

# Database Engine

Primary database:

- Room

Underlying storage:

- SQLite

Requirements:

- WAL (Write-Ahead Logging)
- Foreign key constraints
- Transactions for multi-step operations
- Automatic schema validation

---

# Core Entities

The database consists of the following primary entities:

- Notebook
- Folder
- Page
- Layer
- Stroke
- StrokePoint
- AIAnnotation
- Template
- Attachment
- Tag
- NotebookTag
- SearchIndex
- AppMetadata

---

# Entity: Notebook

Fields:

- notebookId (UUID)
- title
- description
- coverThumbnail
- folderId
- templateId
- color
- createdAt
- updatedAt
- isFavorite
- isArchived
- pageCount

Indexes:

- title
- updatedAt
- isFavorite

---

# Entity: Folder

Fields:

- folderId
- name
- color
- createdAt

Supports nested folders in future versions.

---

# Entity: Page

Fields:

- pageId
- notebookId
- pageNumber
- templateId
- zoomLevel
- canvasWidth
- canvasHeight
- createdAt
- updatedAt

Relationship:

Notebook (1) → (Many) Pages

---

# Entity: Layer

Fields:

- layerId
- pageId
- name
- orderIndex
- visible
- locked
- opacity

Relationship:

Page (1) → (Many) Layers

---

# Entity: Stroke

Fields:

- strokeId
- layerId
- toolType
- color
- width
- opacity
- boundingBox
- createdAt

Relationship:

Layer (1) → (Many) Strokes

---

# Entity: StrokePoint

Stores vector coordinates.

Fields:

- pointId
- strokeId
- sequenceNumber
- x
- y
- pressure
- timestamp

Relationship:

Stroke (1) → (Many) StrokePoints

---

# Entity: AIAnnotation

Fields:

- annotationId
- pageId
- promptSummary
- modelName
- generatedAt
- region
- editable

Relationship:

Page (1) → (Many) AI Annotations

---

# Entity: Template

Fields:

- templateId
- name
- category
- backgroundType
- isDarkVariant

---

# Entity: Attachment

Supports:

- Images
- PDFs
- Future media

Fields:

- attachmentId
- notebookId
- type
- filePath
- importedAt

---

# Entity: Tag

Fields:

- tagId
- name
- color

Many-to-many relationship via NotebookTag.

---

# Entity: SearchIndex

Stores OCR and searchable content.

Fields:

- indexId
- notebookId
- pageId
- recognizedText
- lastIndexedAt

---

# Entity: AppMetadata

Stores internal information:

- schemaVersion
- appVersion
- lastMigration
- databaseCreated

---

# Relationships

Notebook

↓

Pages

↓

Layers

↓

Strokes

↓

StrokePoints

AIAnnotations attach to Pages.

Attachments belong to Notebooks.

Tags connect through NotebookTag.

---

# DAO Responsibilities

Provide DAOs for:

- Notebook
- Folder
- Page
- Layer
- Stroke
- AIAnnotation
- Template
- Attachment
- SearchIndex

Each DAO should expose:

- Insert
- Update
- Delete
- Query
- Observe (Flow)

---

# Transactions

Use Room transactions for:

- Notebook creation
- Notebook deletion
- Import
- Restore
- Bulk stroke insertion
- Export preparation

---

# Indexing Strategy

Create indexes for:

- Notebook title
- Modified date
- Favorite flag
- Page number
- Layer order
- OCR text

Optimize queries for large notebooks.

---

# Migration Strategy

Every schema update must include:

- Version increment
- Migration script
- Data preservation
- Validation tests

Destructive migrations are not permitted in production.

---

# Performance Targets

- Open notebook metadata quickly
- Efficient pagination
- Incremental writes
- Minimize database locks
- Support notebooks containing millions of stroke points

---

# Security

Requirements:

- Validate foreign keys
- Reject malformed data
- Use parameterized queries
- Never expose database internals to UI

---

# Future Expansion

Schema should support:

- Cloud synchronization
- Collaboration
- Version history
- Shared notebooks
- Encryption metadata
- Plugin-defined entities

---

# Acceptance Criteria

The database schema is complete only if:

- Relationships remain consistent.
- Queries scale to large notebooks.
- Migrations preserve user data.
- Database corruption is minimized through transactions and validation.
"""