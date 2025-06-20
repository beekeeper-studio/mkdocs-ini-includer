# Configuration Overview

This page demonstrates how to include entire INI files using the MkDocs INI Includer plugin.

## Complete Application Configuration

Below is the complete configuration file for our demo application. This shows all available settings with their comments and explanations:

{% ini-include %}

## Benefits of Including Full Configuration

Including the complete configuration file provides several advantages:

1. **Comprehensive Documentation**: Users can see all available options in one place
2. **Context Preservation**: Comments and structure from the original file are maintained
3. **Always Up-to-Date**: Documentation automatically reflects changes to the config file
4. **No Duplication**: Single source of truth for configuration documentation

## Configuration Sections

The application configuration is organized into the following main sections:

- **[app]**: Application metadata and feature flags
- **[server]**: Web server and SSL configuration  
- **[database]**: Database connection and replica settings
- **[cache]**: Redis cache configuration
- **[logging]**: Logging levels and output settings
- **[security]**: Authentication, JWT, and CORS settings
- **[email]**: SMTP and email queue configuration
- **[monitoring]**: APM, metrics, and health monitoring
- **[api]**: REST API configuration and rate limiting
- **[features]**: Feature flags and beta settings

For detailed documentation of specific sections, see the individual configuration pages in this section.