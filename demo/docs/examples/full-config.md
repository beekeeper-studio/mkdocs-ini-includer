# Full Configuration Example

This page demonstrates the most basic usage of the MkDocs INI Includer plugin: including an entire configuration file.

## Complete Application Configuration

The following shows our complete `application.ini` file with all sections, comments, and formatting preserved:

{% ini-include %}

## How This Works

The inclusion above was generated using this simple syntax:

```markdown
{% ini-include %}
```

## What Gets Included

When you include a full INI file, the plugin preserves:

✅ **All sections** - Every `[section]` in the file  
✅ **Comments** - Both `#` and `;` style comments  
✅ **Formatting** - Blank lines and indentation  
✅ **Array syntax** - Keys with `[]` notation  
✅ **Environment variables** - `${VAR}` placeholders  

## Use Cases for Full Inclusion

Full configuration inclusion is ideal for:

1. **Reference Documentation**: Complete configuration reference
2. **Getting Started Guides**: Show users all available options
3. **Configuration Templates**: Provide copy-paste ready configs
4. **Troubleshooting**: Help users compare their config with a working example

## File Path Resolution

The plugin looks for files relative to your `docs_dir`, or you can configure a `base_path`:

```yaml
# In mkdocs.yml
plugins:
  - ini-includer:
      base_path: "config"  # Look in docs/config/ directory
```

This allows you to organize your configuration files in a dedicated directory while keeping your documentation structure clean.

## Advantages Over Copy-Paste

Using the plugin instead of copying configuration content provides:

- **Always Current**: Documentation updates automatically when config changes
- **No Duplication**: Single source of truth for configuration
- **Reduced Maintenance**: No need to remember to update docs when config changes
- **Consistency**: Identical formatting between actual config and documentation