## 2025-05-15 - [Credential Hardening & SQL Injection Prevention]
**Vulnerability:** Hardcoded database credentials in ingestion scripts and unsanitized string interpolation in SQL queries.
**Learning:** Hardcoded credentials expose sensitive information, and using f-strings for SQL queries (even for internal data) is a risky pattern that can lead to SQL injection.
**Prevention:** Use environment variables for configuration and always use parameterized queries with SQLAlchemy `text()` and bind parameters. Utilize `sqlalchemy.engine.URL.create` for secure connection string construction. Use `.gitignore` to protect `.env` files.
