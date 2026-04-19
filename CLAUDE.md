# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Spendly** — a Flask-based personal expense tracker. The project is structured as a step-by-step build; many routes and the database layer are stubs that get implemented incrementally.

## Commands

```bash
# Activate virtual environment (Windows)
venv\Scripts\activate

# Run the dev server (port 5001)
python app.py

# Run tests
pytest

# Run a single test file
pytest tests/test_auth.py
```

## Architecture

- **`app.py`** — Flask application entry point; all routes live here. Currently has working routes for `/`, `/register`, `/login`, `/terms`, `/privacy` and stub routes for `/logout`, `/profile`, `/expenses/add`, `/expenses/<id>/edit`, `/expenses/<id>/delete`.
- **`database/db.py`** — SQLite helpers (stub). Must implement: `get_db()` (connection with `row_factory` and foreign keys), `init_db()` (CREATE TABLE IF NOT EXISTS), `seed_db()` (dev data).
- **`templates/base.html`** — Jinja2 base template with navbar and footer. All pages extend this via `{% block content %}`.
- **`static/css/style.css`** — global styles; `static/css/landing.css` — landing page-specific styles.
- **`static/js/main.js`** — client-side JS, populated as features are built.

## Key Conventions

- Database is SQLite; access via `get_db()` from `database/db.py` — do not open raw `sqlite3` connections in routes.
- Templates use Jinja2 `url_for()` for all internal links (never hardcode paths except in the footer links which currently do).
- App runs on port 5001 (`debug=True` in dev).
- `pytest` + `pytest-flask` are the test stack; no test files exist yet.
