## 2026-06-15 - [Initial Security Audit]
**Vulnerability:** Hardcoded database credentials and SQL injection risks via string interpolation in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`.
**Learning:** Legacy ingestion scripts often prioritize ease of use over security, leading to hardcoded secrets and unsafe SQL practices.
**Prevention:** Use environment variables for secrets, `sqlalchemy.engine.URL.create` for safe URL construction, and parameterized queries for all database operations.
