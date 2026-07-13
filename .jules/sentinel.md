## 2026-06-18 - Fix SQL Injection and Hardcoded Credentials
**Vulnerability:** SQL injection in metadata table insertion and hardcoded database credentials in scripts.
**Learning:** Metadata tables like `_referencia` were historically populated using f-string interpolation for variables like `dataReferencia`, creating SQL injection risks. Hardcoded credentials pose a secret exposure risk.
**Prevention:** Use SQLAlchemy `text()` with bind parameters for all SQL queries. Use environment variables (via a `.env` file) to manage sensitive configuration, and ensure `.env` is ignored by version control.
