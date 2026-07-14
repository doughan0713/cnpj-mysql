## 2024-07-14 - Fix SQL injection and hardcoded credentials
**Vulnerability:** Hardcoded database credentials in ingestion scripts and SQL injection risk in metadata tables using f-string interpolation.
**Learning:** Metadata tables like `_referencia` were historically populated using f-string interpolation for variables like `dataReferencia`, creating SQL injection risks. Additionally, hardcoded credentials prevent secure environment management.
**Prevention:** Use `sqlalchemy.engine.URL.create` for secure connection string construction and always use parameterized queries with `text()` and bind parameters, even for internal metadata. Implement a `.env` loader to externalize secrets.
