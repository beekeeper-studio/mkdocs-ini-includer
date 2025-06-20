# MkDocs INI Includer Demo

Welcome to the demonstration site for the **MkDocs INI Includer** plugin!

## What is MkDocs INI Includer?

MkDocs INI Includer is a plugin that allows you to include INI configuration files (or specific sections) directly in your MkDocs documentation. This is particularly useful for:

- 📚 **Documentation**: Keep your config docs in sync with actual config files
- 🔧 **Configuration Management**: Show real configuration examples
- 🎯 **Specific Features**: Document particular config sections without duplication

## Demo Configuration

This demo site uses a complex application configuration file located at `config/application.ini`. The configuration includes:

- **Application Settings**: Basic app metadata and feature flags
- **Server Configuration**: Web server, SSL, and request handling
- **Database Setup**: Primary database and read replica configuration
- **Caching**: Redis cache configuration
- **Logging**: Comprehensive logging setup
- **Security**: Authentication, JWT, rate limiting, and CORS
- **Email Service**: SMTP configuration and queue settings
- **Monitoring**: APM, metrics, and health checks
- **API Configuration**: REST API settings and authentication
- **Feature Flags**: Toggleable application features

## Navigation

Use the navigation menu to explore different sections:

- **Configuration**: Detailed documentation of specific config sections
- **Examples**: Practical examples showing the plugin in action

## Plugin Usage Examples

Throughout this demo, you'll see the plugin used in two main ways:

### Include Full File
```markdown
{% ini-include %}
```

### Include Specific Section
```markdown
{% ini-include section=database %}
```

Let's get started! Navigate to the [Configuration Overview](config/overview.md) to see the plugin in action.