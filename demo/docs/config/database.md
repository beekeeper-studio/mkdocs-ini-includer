# Database Configuration

This page demonstrates including specific sections of an INI file. Here we focus on database-related configuration.

## Primary Database Settings

The main database configuration includes connection details, pooling, and query settings:

{% ini-include section=database %}

## Key Database Settings Explained

### Connection Details
- **driver**: PostgreSQL is used as the primary database
- **host/port**: Connection endpoint for the database server
- **database**: Name of the application database
- **username**: Database user for the application

### Connection Pooling
Connection pooling is crucial for performance:

- **pool_min**: Minimum connections maintained (5)
- **pool_max**: Maximum concurrent connections (20)  
- **pool_timeout**: Timeout for acquiring a connection (30s)
- **pool_recycle**: Connection lifetime before recycling (1 hour)

### Query Performance
- **query_timeout**: Maximum time for query execution (30s)
- **slow_query_threshold**: Log queries taking longer than 1000ms

## Read Replica Configuration

For improved read performance, a read replica is configured:

{% ini-include section=database.replica %}

The read replica uses:
- A separate host (`db-replica.example.com`)
- Read-only user account
- Smaller connection pool for read operations
- Same database name and port as primary

## Environment Variables

Note that sensitive information like passwords should be provided via environment variables:
- `DB_PASSWORD`: Password for the primary database user
- Database passwords are referenced as `${DB_PASSWORD}` in the config

## Best Practices

1. **Use Connection Pooling**: Reduces connection overhead and improves performance
2. **Separate Read/Write**: Use read replicas for read-heavy operations
3. **Environment Variables**: Never store passwords in configuration files
4. **Monitor Slow Queries**: Set appropriate thresholds for query performance monitoring
5. **Connection Limits**: Set reasonable pool limits based on your database server capacity