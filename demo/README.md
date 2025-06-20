# MkDocs INI Includer Demo

This directory contains a comprehensive demonstration of the MkDocs INI Includer plugin.

## What's Included

- **Complex Configuration**: `config/application.ini` - A realistic application configuration with multiple sections
- **Demo Site**: Complete MkDocs site showing the plugin in action
- **Multiple Examples**: Both full file inclusion and section-specific inclusion

## Configuration File

The demo uses `config/application.ini` which includes:

- Application metadata and feature flags
- Web server and SSL configuration
- Database connection and replica settings  
- Redis cache configuration
- Comprehensive logging setup
- Security settings (JWT, CORS, rate limiting)
- Email service configuration
- Monitoring and APM settings
- REST API configuration
- Feature flags and toggles

## Plugin Configuration

The demo site is configured in `mkdocs.yml` with:

```yaml
plugins:
  - ini-includer:
      base_path: "config"              # Look in config/ directory
      config_file: "application.ini"  # Default file for includes
```

## Running the Demo

1. **Install Dependencies**:
   ```bash
   pip install mkdocs mkdocs-material
   pip install -e ../  # Install the plugin from parent directory
   ```

2. **Serve the Demo**:
   ```bash
   mkdocs serve
   ```

3. **Build the Demo**:
   ```bash
   mkdocs build
   ```

## Demo Pages

- **Home**: Introduction and overview
- **Configuration Overview**: Shows full file inclusion
- **Database**: Focused on database configuration sections
- **Security**: Security-related configuration
- **API**: API configuration settings
- **Full Config Example**: Complete configuration with explanations
- **Partial Includes**: Multiple section examples

## Plugin Syntax Examples

### Include Entire File
```markdown
{% ini-include %}
```

### Include Specific Section
```markdown
{% ini-include section=database %}
```

### Override Default File
```markdown
{% ini-include file="other-config.ini" section=api %}
```

## Key Features Demonstrated

- **Default Configuration**: No need to specify file on every include
- **Section Filtering**: Include only relevant configuration sections
- **Comment Preservation**: Comments from INI files are maintained
- **Array Support**: INI array syntax (`key[] = value`) is preserved
- **Hierarchical Sections**: Sub-sections are included with parent sections
- **Error Handling**: Graceful handling of missing files or sections

## File Structure

```
demo/
├── README.md                    # This file
├── mkdocs.yml                   # Demo site configuration
├── config/
│   └── application.ini          # Demo configuration file
└── docs/
    ├── index.md                 # Home page
    ├── config/
    │   ├── overview.md          # Full config inclusion
    │   ├── database.md          # Database sections
    │   ├── security.md          # Security configuration
    │   └── api.md              # API settings
    └── examples/
        ├── full-config.md       # Complete file example
        └── partial-includes.md  # Section examples
```

This demo provides a realistic example of how to use the MkDocs INI Includer plugin to maintain synchronized documentation for complex application configurations.