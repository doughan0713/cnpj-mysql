## 2026-07-20 - Parameterized Reference Insertion and Safe URL Construction
**Vulnerability:** SQL Injection (SQLi) in metadata table insertion due to f-string interpolation, and risks of insecure URL structure when constructing database engines.
**Learning:** Hardcoding credentials or using simple f-string concatenations for SQL queries and URL building can expose the database to credentials leak or injection vulnerabilities.
**Prevention:** Always construct database URLs using `sqlalchemy.engine.URL.create` to safely handle passwords/special characters, read parameters from environment variables (avoiding hardcoded secrets), and use SQLAlchemy `text()` bind parameters (`:param_name`) to parameterize all queries.
