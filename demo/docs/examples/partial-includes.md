# Partial Configuration Includes

This page demonstrates including specific sections of an INI file, which is perfect for focused documentation.

## Database Configuration Only

Sometimes you only want to show relevant configuration sections. Here's just the database configuration:

{% ini-include section=database %}

## Cache Configuration

And here's just the cache configuration:

{% ini-include section=cache %}

## Server Configuration

Web server and SSL settings:

{% ini-include section=server %}

## How Partial Includes Work

Each inclusion above uses the `section` parameter:

```markdown
{% ini-include section=database %}
{% ini-include section=cache %}
{% ini-include section=server %}
```

## Section Matching Rules

The plugin includes sections using these rules:

1. **Exact Match**: `section="database"` includes `[database]`
2. **Hierarchical Match**: `section="database"` also includes `[database.replica]`
3. **Comments Preserved**: Comments within the section are included
4. **Formatting Maintained**: Blank lines and structure are preserved

## Multiple Related Sections

When you specify a section like `database`, you get:

- `[database]` - The main section
- `[database.replica]` - Any sub-sections
- `[database.ssl]` - Additional sub-sections (if they existed)

This makes it easy to document related configuration groups together.

## Security Section Example

Here's the security configuration which includes CORS settings:

{% ini-include section=security %}

Notice how this includes all the CORS arrays and sub-settings that belong to the security section.

## Monitoring Configuration

Application monitoring and health check settings:

{% ini-include section=monitoring %}

## Benefits of Partial Includes

Partial includes are perfect for:

1. **Focused Documentation**: Show only relevant configuration for specific topics
2. **Organized Docs**: Break large configurations into digestible sections  
3. **Context-Specific**: Include database config on database pages, API config on API pages
4. **Reduced Noise**: Hide irrelevant settings that might confuse users
5. **Better Navigation**: Users can find specific configuration more easily

## Advanced Usage Tips

### Combining Multiple Sections

You can include multiple related sections on the same page:

```markdown
## Database Settings
{% ini-include section=database %}

## Cache Settings  
{% ini-include section=cache %}
```

### Documentation Structure

A good pattern is to:
1. Use full includes for reference pages
2. Use partial includes for feature-specific documentation
3. Combine partial includes when documenting related features
4. Add explanatory text around each inclusion to provide context

This approach gives you the flexibility to create both comprehensive reference documentation and focused, task-oriented guides.