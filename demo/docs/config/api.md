# API Configuration

The application provides a RESTful API with comprehensive configuration options.

## API Settings

{% ini-include section=api %}

## API Configuration Details

### Version and Routing
- **version**: Current API version (v1)
- **base_path**: All API endpoints are prefixed with `/api/v1`
- **documentation_enabled**: Swagger/OpenAPI documentation is available
- **documentation_path**: API docs accessible at `/docs`

### Rate Limiting
The API has its own rate limiting that can override global settings:
- **rate_limit_requests**: 1000 requests per hour (more generous than global)
- **rate_limit_window**: 3600 seconds (1 hour window)

### Authentication
- **auth_required**: All API endpoints require authentication
- **auth_methods[]**: Supports both JWT tokens and API keys

### Pagination
- **default_page_size**: 20 items per page by default
- **max_page_size**: Maximum of 100 items per page
- **include_metadata**: Responses include pagination metadata

## Authentication Methods

The API supports two authentication methods:

=== "JWT Authentication"
    ```http
    GET /api/v1/users
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
    ```

=== "API Key Authentication"
    ```http
    GET /api/v1/users
    X-API-Key: your-api-key-here
    ```

## API Response Format

All API responses follow a consistent format:

```json
{
  "data": [...],
  "meta": {
    "page": 1,
    "per_page": 20,
    "total": 150,
    "total_pages": 8
  }
}
```

## Rate Limiting Headers

API responses include rate limiting information:

```http
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1640995200
```

## Error Responses

The API returns structured error responses:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid request parameters",
    "details": [
      {
        "field": "email",
        "message": "Invalid email format"
      }
    ]
  }
}
```

## API Documentation

With `documentation_enabled = true`, the API automatically generates:

- **Swagger UI**: Interactive API documentation
- **OpenAPI Spec**: Machine-readable API specification
- **Code Examples**: Generated client code snippets

Access the documentation at: `https://your-domain.com/docs`

## Usage Examples

### List Users (Paginated)
```bash
curl -H "Authorization: Bearer $JWT_TOKEN" \
     "https://api.example.com/api/v1/users?page=1&per_page=20"
```

### Create User
```bash
curl -X POST \
     -H "Authorization: Bearer $JWT_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"name":"John Doe","email":"john@example.com"}' \
     "https://api.example.com/api/v1/users"
```

### Using API Key
```bash
curl -H "X-API-Key: your-api-key" \
     "https://api.example.com/api/v1/users"
```