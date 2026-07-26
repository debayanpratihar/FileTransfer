
# AI Notebook — Claude Code Entry Point

Version: 1.0

## Purpose

This is the **entry point** for Claude Code.

Before writing **any code**, read every document in the `AI-NOTEBOOK-SPEC` folder. These documents together define the complete product specification. Treat them as the single source of truth.

---

# Rules

1. Read every Markdown file before making implementation decisions.
2. Do not skip documents.
3. If two documents appear to conflict:
   - Prefer the lower-numbered document.
   - If still ambiguous, explain the issue and request clarification instead of guessing.
4. Do not invent major features that are not described in the specifications.
5. Keep the project offline-first and privacy-first.
6. Maintain Clean Architecture throughout the codebase.

---

# Read Order

Read the specification files in numerical order:

00_MASTER_PROMPT.md

01_PRODUCT_VISION.md

02_REQUIREMENTS.md

03_UI_UX_SPEC.md

04_CANVAS_ENGINE.md

05_DRAWING_ENGINE.md

06_HANDWRITING_ENGINE.md

07_AI_ENGINE.md

08_MODEL_MANAGER.md

09_NOTEBOOK_STORAGE.md

10_OCR_AND_DOCUMENT_AI.md

11_SETTINGS_AND_PREFERENCES.md

12_EXPORT_IMPORT_SYSTEM.md

13_APPLICATION_ARCHITECTURE.md

14_DATABASE_SCHEMA.md

15_PROJECT_STRUCTURE.md

16_TESTING_STRATEGY.md

17_SECURITY_AND_PRIVACY.md

18_PERFORMANCE_OPTIMIZATION.md

19_DEPLOYMENT_AND_RELEASE.md

20_ROADMAP_AND_FUTURE_FEATURES.md

21_API_AND_JSON_SPEC.md (if present)

22_CLAUDE_CODE_IMPLEMENTATION_GUIDE.md

23_RELEASE_CHECKLIST.md (if present)

24_TODO_AND_BACKLOG.md

---

# Required Technology Stack

- Kotlin
- Jetpack Compose
- Material 3
- Clean Architecture
- MVVM
- Hilt
- Room
- DataStore
- WorkManager
- ML Kit
- llama.cpp
- GGUF Models

Do not replace these technologies without explicit approval.

---

# Development Workflow

Before coding:

1. Read all specifications.
2. Summarize your understanding.
3. Identify missing information or conflicts.
4. Produce an implementation roadmap.
5. Wait for approval.

During implementation:

- Complete one phase at a time.
- Keep changes small and reviewable.
- Explain completed work before moving on.
- Update documentation if implementation changes behaviour.
- Add tests alongside new business logic.

---

# Definition of Done

A task is complete only when:

- Code builds successfully.
- Tests pass.
- Lint passes.
- Documentation is updated.
- No critical issues remain.
- Implementation matches the specification.

---

# Primary Objective

Build a production-quality Android application that faithfully implements the AI Notebook specifications while remaining:

- Offline-first
- Privacy-first
- Scalable
- Maintainable
- Performant
- Secure

If a specification is unclear, ask for clarification instead of making assumptions.
""")

