## 2026-07-08 - [Secure Database Configuration and Query Parameterization]
**Vulnerability:** Hardcoded database credentials and SQL injection via string formatting in database ingestion scripts.
**Learning:** Legacy scripts often use string interpolation for SQL queries and hardcoded configuration, making them vulnerable to injection and credential leakage.
**Prevention:** Use environment variables for configuration and ALWAYS use parameterized queries with SQLAlchemy's `text()` and bind parameters. Construct connection URLs using `sqlalchemy.engine.URL.create` to handle special characters securely.
