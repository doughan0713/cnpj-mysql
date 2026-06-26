## 2025-05-15 - [Securing Database Connections and Queries]
**Vulnerability:** Hardcoded database credentials and SQL injection via string interpolation in DDL and DML statements.
**Learning:** Ingestion scripts often contain hardcoded defaults for ease of use, which can lead to accidental credential exposure. SQL injection risks are common when developers use f-strings for queries, even when using libraries like SQLAlchemy.
**Prevention:** Use environment variables for all sensitive configurations and provide a `.env.example` template. Always use parameterized queries (bind parameters) with `sqlalchemy.text()` for DML. For DDL where parameterization isn't supported, ensure identifiers are from trusted sources. Use `sqlalchemy.engine.URL.create` to safely build connection strings.
