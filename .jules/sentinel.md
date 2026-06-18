## 2025-05-14 - Use of `sqlalchemy.engine.URL.create` for Secure Database Connections
**Vulnerability:** Hardcoded database credentials and insecure connection string construction via f-strings.
**Learning:** Hardcoding credentials makes the code inflexible and insecure. Using f-strings to build connection URLs can fail if passwords contain special characters (e.g., `@`, `:`, `/`) and is less robust than using library-provided URL builders.
**Prevention:** Always use `os.getenv()` for configuration and leverage `sqlalchemy.engine.URL.create()` (or equivalent for other libraries) to safely construct connection strings.

## 2025-05-14 - Fully Parameterized Queries in SQLAlchemy
**Vulnerability:** Use of f-strings for SQL query parameters, even for seemingly safe data.
**Learning:** While the risk might be low for some internal variables, it's a best practice for a "Sentinel" to model perfect security by using parameterized queries for *all* dynamic input in SQL statements.
**Prevention:** Use `sqlalchemy.text()` with bind parameters (e.g., `:param`) and provide a dictionary of values to `engine.execute()`.
