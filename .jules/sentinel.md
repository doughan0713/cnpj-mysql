## 2025-05-14 - Secure Database Ingestion
**Vulnerability:** Hardcoded database credentials and SQL injection via f-strings in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`.
**Learning:** Credentials were hardcoded for developer convenience, and f-strings were used for SQL construction in the `_referencia` table insertion, which is a potential SQL injection vector.
**Prevention:** Always use environment variables for secrets and use parameterized queries (bind parameters) for all SQL execution. Use `sqlalchemy.engine.URL.create` for secure connection string construction.
