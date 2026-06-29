## 2024-06-29 - Hardcoded Credentials and SQL Injection in Ingestion Scripts
**Vulnerability:** Hardcoded database credentials (username, password) and SQL injection via f-strings in `engine.execute` calls.
**Learning:** The application lacked a configuration management system, leading to secrets being stored in source code. SQL queries were constructed using string interpolation, which is a classic injection vector.
**Prevention:** Use environment variables for all configuration and secrets. Always use parameterized queries with SQLAlchemy `text()` and bind parameters. Construct connection URLs using `sqlalchemy.engine.URL.create` to handle special characters securely.
