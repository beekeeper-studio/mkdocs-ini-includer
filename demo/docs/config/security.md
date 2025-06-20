# Security Configuration

Security is critical for any application. This page shows how to document security configurations using specific INI sections.

## Core Security Settings

{% ini-include section=security %}

## Security Features Breakdown

### Session Management
- **secret_key**: Cryptographic key for session signing (use environment variable)
- **session_timeout**: Sessions expire after 1 hour (3600 seconds)
- **csrf_protection**: Cross-Site Request Forgery protection enabled
- **xss_protection**: Cross-Site Scripting protection enabled

### JWT Authentication
JSON Web Tokens are configured for API authentication:
- **jwt_algorithm**: HMAC SHA-256 for token signing
- **jwt_expiration**: Access tokens expire after 30 minutes
- **jwt_refresh_expiration**: Refresh tokens valid for 7 days

### Rate Limiting
Prevents abuse and DoS attacks:
- **rate_limit_enabled**: Rate limiting is active
- **rate_limit_requests**: 100 requests allowed per window
- **rate_limit_window**: 60-second time window
- **rate_limit_storage**: Uses Redis for distributed rate limiting

### CORS Configuration
Cross-Origin Resource Sharing settings:
- **cors_enabled**: CORS support is active
- **cors_origins[]**: Array of allowed origins
- **cors_methods[]**: Permitted HTTP methods
- **cors_headers[]**: Allowed request headers

## Security Best Practices

!!! warning "Important Security Notes"
    - Never store secrets directly in configuration files
    - Use environment variables for sensitive data
    - Regularly rotate JWT signing keys
    - Monitor rate limiting metrics
    - Keep CORS origins as restrictive as possible

!!! tip "Environment Variables"
    The following environment variables should be set:
    - `SECRET_KEY`: Application secret key
    - `JWT_SECRET`: JWT signing key (if different from SECRET_KEY)

## CORS Origins

The application allows requests from these origins:

```ini
cors_origins[] = "https://example.com"
cors_origins[] = "https://demo.example.com"
```

This array syntax in INI files is preserved by the plugin, showing exactly how the configuration should be structured.

## Rate Limiting Strategy

The rate limiting configuration uses a sliding window approach:
1. Tracks requests per IP address
2. Allows 100 requests per 60-second window
3. Stores counters in Redis for scalability
4. Returns HTTP 429 when limits are exceeded

## Implementation Notes

- Rate limiting works across multiple application instances when using Redis
- CORS preflight requests are handled automatically
- JWT tokens should be sent in the `Authorization` header as `Bearer <token>`
- Session cookies are signed with the secret key and include CSRF tokens