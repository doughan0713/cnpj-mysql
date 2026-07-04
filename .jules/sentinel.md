## 2025-07-04 - [Fix hardcoded secrets and SQL injection]
**Vulnerability:** Database credentials were hardcoded in ingestion scripts, and SQL queries were using f-string interpolation for values, leading to potential SQL injection.
**Learning:** Legacy scripts often have hardcoded credentials and lack parameterization. Using SQLAlchemy's `URL.create` and `text()` with bind parameters provides a robust defense.
**Prevention:** Always use environment variables for secrets and parameterized queries for SQL execution. Implement a simple `.env` loader if external dependencies are restricted.
