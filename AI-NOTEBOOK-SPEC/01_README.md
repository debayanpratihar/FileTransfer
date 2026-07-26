# AI Notebook - Master Product Specification

# IMPORTANT

Before writing any code, read EVERY markdown file inside the `/docs` directory.

Never ignore the specifications.

This project is intended to become one of the best AI-powered note-taking applications available on Android.

Do not simplify features unless explicitly instructed.

Do not replace professional implementations with placeholders.

Every implementation must be production-ready.

---

# Project Overview

AI Notebook is a completely offline-first intelligent notebook application for Android.

Unlike ChatGPT, Gemini, or Copilot, the AI does NOT communicate inside a chat window.

Instead...

The AI writes naturally inside the notebook itself exactly like another human writing beside the user.

The notebook is the interface.

The AI is simply another writer inside that notebook.

The experience should feel similar to writing together on a real notebook.

---

# Main Philosophy

Privacy First

Everything should work without internet after the AI model has been downloaded.

No handwritten notes should ever leave the device.

No OCR results should leave the device.

No AI prompts should leave the device.

Internet is only used for:

• Downloading AI models

• Checking GitHub configuration files

• Future optional update checks

Everything else must remain local.

---

# Target Users

Students

Teachers

Software Engineers

Researchers

Doctors

Architects

Designers

Business Professionals

Mathematicians

Anyone who takes handwritten notes.

---

# Supported Platform

Current Target

Android only.

Future

Android Tablets

Chromebooks

Foldables

Eventually

iPad

Desktop

The architecture should be scalable enough to support future platforms.

---

# Design Goal

The application should feel like a combination of

GoodNotes

Notability

OneNote

Concepts

Samsung Notes

combined with

Local AI.

---

# Core Experience

User opens notebook.

User starts writing.

User draws diagrams.

User inserts images.

User imports PDFs.

Whenever the user wants...

AI can help.

The AI writes directly onto the notebook.

Not inside a popup.

Not inside a chat.

The notebook itself is the conversation.

---

# AI Behaviour

AI should never interrupt the user.

AI should never start writing unless:

Automatic Generation is enabled

OR

The user presses Generate.

The user must always have full control.

---

# Automatic AI

The application must have a switch:

Automatic AI

ON

↓

Whenever the user stops writing for a configurable duration

AI starts solving.

Automatic AI

OFF

↓

AI never generates automatically.

Only Generate button works.

This setting must be remembered.

---

# AI Writing

AI should look like it is actually writing.

Not instantly appearing.

The writing should animate.

Stroke by stroke.

Letter by letter.

The animation speed should be configurable.

---

# AI Placement

AI should intelligently determine where to place the answer.

Priority

1.

Right side of existing content.

2.

Below existing content.

3.

Create continuation area.

Never overwrite user handwriting.

Never cover drawings.

Never cover images.

Never cover PDFs.

---

# AI Style

User should be able to choose:

Normal handwriting

Neat handwriting

Printed handwriting

Technical handwriting

Mathematical handwriting

Marker style

Blue ink

Black ink

Red ink

Green ink

Pencil

The AI should respect notebook settings.

---

# Offline Models

AI runs using GGUF models.

Inference engine

llama.cpp

Models are downloaded from Hugging Face.

Configuration comes from GitHub Pages.

Configuration URL

https://debayanpratihar.github.io/ai-notebook-config/

The app already contains

config.json

models.json

announcements.json

changelog.json

These files determine

Available models

Announcements

Application configuration

Version information

Claude must build the application around this existing infrastructure.

---

# AI Models

Compact

Qwen2.5-1.5B

Balanced

Qwen2.5-3B

High Quality

Qwen2.5-7B

The application should automatically recommend the best model based on

RAM

Storage

CPU

ABI

Android version

The user can override the recommendation.

---

# Development Rules

Use

Kotlin

Jetpack Compose

Material 3

Clean Architecture

MVVM

Repository Pattern

Room

DataStore

Hilt

Coroutines

Flow

WorkManager

OkHttp

ML Kit

llama.cpp

No XML layouts.

Compose only.

No placeholder implementations.

No TODO code.

Every class should be production ready.

---

# Performance Goals

Drawing latency

<16 ms

Notebook opening

<500 ms

Page switching

<200 ms

Zoom

60 FPS minimum

Stylus latency

As low as possible.

AI inference should never freeze the UI.

---

# Code Quality

Readable

Modular

Scalable

Testable

Maintainable

No God classes.

No duplicated logic.

Use dependency injection.

Use interfaces.

Separate UI from business logic.

---

# Future Expansion

Claude should design the architecture so that future additions require minimal modification.

Possible future features include

Cloud sync

Team collaboration

Voice notes

Audio transcription

Screen recording

Lecture mode

Plugin system

AI agents

Custom AI models

Multi-model support

Handwriting search

Formula recognition

Real-time collaboration

Cross-platform support

These future possibilities should influence architecture decisions.

---

# Mission

The goal is NOT simply to build another notes application.

The goal is to build the best offline AI notebook for Android.

Every decision should prioritize

Performance

Privacy

User experience

Scalability

Professional quality

Long-term maintainability.

Claude should think like a senior Android architect building a flagship application rather than a prototype.

Never sacrifice architecture for short-term convenience.