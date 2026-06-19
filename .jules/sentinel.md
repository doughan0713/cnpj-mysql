## 2024-05-16 - Parameterized Queries and Secure URL Construction
**Vulnerability:** SQL injection via f-strings in database insertions and potential credentials injection via f-string URL construction.
**Learning:** Using SQLAlchemy's `URL.create` is safer than f-strings for building connection strings as it handles special characters and escaping. Parameterizing queries even for "low-risk" reference tables is a best practice to maintain consistency.
**Prevention:** Always use `sqlalchemy.engine.URL.create` and parameterized `text()` queries with bind parameters.
