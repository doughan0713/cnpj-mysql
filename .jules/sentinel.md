## 2026-06-25 - SQL Injection in Metadata Insertion
**Vulnerability:** The data ingestion scripts (`dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`) were historically populating metadata tables like `_referencia` using f-string interpolation for variables like `dataReferencia`, creating SQL injection risks.
**Learning:** Even internal script variables derived from processed files or inputs must be treated with zero-trust principles. Using f-strings to build SQL queries is a critical security vulnerability that can be exploited if file metadata is manipulated.
**Prevention:** Always use parameterized queries with SQLAlchemy `text()` and bind parameter dictionaries (e.g., using `:dataReferencia` and `:qtde_cnpjs`) for any dynamic SQL value insert or filter statement.
