# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website ("delta") deployed on Vercel as a Python serverless function using Flask.

## Architecture

- **Vercel serverless**: All requests rewrite to `/api/index` via `vercel.json`
- **Flask app**: `api/index.py` is the single entry point with one route (`/`) that renders `api/templates/index.html`
- **Static assets**: `api/static/` serves media files (audio, video) — referenced via `/static/` paths in HTML
- **Data**: `api/songs.json` contains a song collection (not currently rendered on the page)
- **Single dependency**: Flask 3.0.3 (`requirements.txt`)

## Development

```bash
# Run locally
python api/index.py
# Serves on http://localhost:8080

# Deploy (via Vercel CLI or git push to connected repo)
vercel
```

## Key Conventions

- Templates use Jinja2 (Flask's default) and live in `api/templates/`
- The site is a single-page design with inline CSS and JS in the HTML template
- No build step, test suite, or linter is configured
