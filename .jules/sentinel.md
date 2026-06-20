## 2024-06-20 - [Secure Database Connection and Parameterized Queries]
**Vulnerability:** Hardcoded database credentials and insecure connection string construction via f-strings. Potential for SQL injection in metadata table insertions.
**Learning:** Hardcoding credentials makes the application fragile and insecure. Using f-strings for connection URLs can fail or be exploited if credentials contain special characters.
**Prevention:** Use environment variables for all sensitive configuration. Use `sqlalchemy.engine.URL.create` to safely build connection URLs and always use parameterized queries with bind parameters for all SQL execution.
