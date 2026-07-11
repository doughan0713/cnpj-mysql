## 2025-05-22 - Insecure database connection handling and SQL construction
**Vulnerability:** Hardcoded database credentials and SQL injection via f-string interpolation in table insertions.
**Learning:** Legacy data ingestion scripts often contain hardcoded defaults and use string interpolation for SQL queries, which poses a significant security risk if deployed in production environments or when processing untrusted metadata.
**Prevention:** Always use environment variables for credentials and use parameterized queries (bind parameters) for all SQL executions, even for internal metadata. Use `sqlalchemy.engine.URL.create` for robust connection string generation.
