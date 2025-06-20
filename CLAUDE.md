# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a MkDocs plugin called `mkdocs-ini-includer` that allows MkDocs sites to embed INI file content directly into documentation at build time. The plugin supports including entire INI files or specific sections while preserving comments and formatting.

## Architecture

### Core Components

- `mkdocs_ini_includer/plugin.py` - Main plugin class (`IniIncluderPlugin`) that extends MkDocs `BasePlugin`
- `mkdocs_ini_includer/__init__.py` - Package initialization and version definition
- `setup.py` - Python package configuration with MkDocs plugin entry point
- `demo/` - Complete working example with sample INI files and MkDocs site

### Plugin Architecture

The plugin works by:
1. Registering as a MkDocs plugin via `on_page_markdown` hook
2. Using regex to find `{% ini-include %}` tags in markdown content
3. Parsing tag arguments to determine file path and optional section filtering
4. Reading INI files with preserved comments (not using configparser for parsing)
5. Filtering content by section if specified (supports nested sections like `database.ssl`)
6. Wrapping output in markdown code blocks with `ini` syntax highlighting

### Key Methods

- `on_page_markdown()` - Main hook that processes markdown content
- `_parse_include_args()` - Parses arguments from include tags
- `_get_full_path()` - Resolves file paths using base_path config
- `_read_ini_with_comments()` - Reads raw INI content preserving formatting
- `_filter_section()` - Extracts specific sections and subsections

## Development Commands

### Package Installation
```bash
pip install -e .  # Install in development mode
```

### Testing with Demo
```bash
cd demo
mkdocs serve  # Run demo site locally
mkdocs build  # Build demo site
```

### Distribution
```bash
python setup.py sdist bdist_wheel  # Build distribution packages
```

## Configuration

Plugin accepts two optional configuration parameters:
- `base_path` - Base directory for INI files (relative to docs_dir)
- `config_file` - Default INI file when none specified in include tag

## Tag Syntax

- `{% ini-include %}` - Include default config file
- `{% ini-include file="path/to/file.ini" %}` - Include specific file
- `{% ini-include section="database" %}` - Include specific section
- `{% ini-include file="config.ini" section="api" %}` - Combine parameters

Section filtering supports hierarchical sections (e.g., `database` includes `database.ssl`).