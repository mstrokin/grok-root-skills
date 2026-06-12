# Grok Skills Directory

## Origin

These files comprise the [`skills/`](skills/) directory extracted from **xAI's Grok** platform — an AI chatbot that provisions a **2 GB RAM, 2 vCPU VPS** on demand for code execution. The VPS runs a **hardened container** with no general internet access. The only network connectivity permitted is for fetching cryptocurrency and stock prices via pre-configured Polygon.io and CoinGecko API proxies.

## Skills Overview

Each skill is a modular instruction package that specializes the Grok agent for a specific task domain. Every skill has a [`SKILL.md`](skills/color/SKILL.md) file with frontmatter + instructions, and may include `scripts/`, `references/`, and templates.

---

### [color](skills/color/SKILL.md) — Color Accessibility Auditing

Python scripts for WCAG contrast checking, color extraction from images, palette generation, and color-vision-deficiency (CVD) simulation.

### [docx](skills/docx/SKILL.md) — Word Document Processing

Create, read, edit, and manipulate `.docx`/`.dotx` files. Scripts for text replacement, field updating, section deletion, tracked-changes acceptance, XML unpack/pack/validate via the shared Office infrastructure, and legacy `.doc` conversion via LibreOffice.

### [ffmpeg](skills/ffmpeg/SKILL.md) — Media Processing

Safety-wrapped FFmpeg/FFprobe usage: format conversion, trimming, resizing, audio extraction, GIF creation, subtitles, overlays, concatenation, with temp-file verification and no-overwrite defaults.

### [finance](skills/finance/SKILL.md) — Financial Market Data

Python queries to Polygon.io (US equities, options, dividends, splits) and CoinGecko (cryptocurrency prices, market caps, historical data). This is the **only network-accessible feature** — API proxies are pre-configured and no general internet is available.

### [imagemagick](skills/imagemagick/SKILL.md) — Image Processing

Safety-wrapped ImageMagick usage with sandbox policy enforcement: resize, crop, format conversion, watermarking, compositing, montages, collages, batch processing with memory limits.

### [mcp](skills/mcp/SKILL.md) — MCP (Model Context Protocol) CLI

Interface for discovering and invoking connected apps (Linear, Slack, GitHub, Google Drive, SharePoint, etc.) via the `grok-mcp` CLI with JSONL output.

### [memory-edit](skills/memory-edit/SKILL.md) — User Memory Policy

Policy defining what the agent should store in user memory (identity, preferences, health) vs. reject (credentials, ephemeral states, third-party data).

### [pdf](skills/pdf/SKILL.md) — PDF Processing

Read, merge, split, rotate, OCR, fill forms, and render PDFs using `pypdf` and `pdfplumber`. Includes IRS 2025 tax form templates and form-field manipulation scripts.

### [pptx](skills/pptx/SKILL.md) — PowerPoint Presentations

Create, edit, and QA `.pptx` files. Scripts for slide add/delete, text replacement, overlap detection with auto-fix, font detection, thumbnail generation, and 20+ pre-built presentation templates.

### [skill-creator](skills/skill-creator/SKILL.md) — Skill Development

Bootstrap and validate new skills with init/validation shell scripts. Enforces YAML frontmatter rules (naming, description formatting, allowed keys).

### [skill-installer](skills/skill-installer/SKILL.md) — Skill Distribution

Install skills from GitHub repositories into `.grok/skills/`. Supports public repos (zip download) and private repos (git sparse-checkout). Validates that installed directories contain `SKILL.md`.

### [tasks](skills/tasks/SKILL.md) — Scheduled Tasks & Reminders

CRUD interface for scheduled Grok tasks with RFC 5545 RRULE cadence support. Create, list, update, pause/resume, delete tasks, and fetch execution results.

### [xlsx](skills/xlsx/scripts/recalc.py) — Excel Formula Recalculation

Python script that recalculates all formulas in an Excel file using LibreOffice's StarBasic macro engine. Shares the Office infrastructure with docx/pptx.
