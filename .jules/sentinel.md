## 2026-07-02 - SQL Injection in Metadata Table Population
**Vulnerability:** In SQL ingestion scripts (`dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`), metadata/reference tables like `_referencia` are populated using direct f-string string interpolation (e.g., `f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')"`) which creates an SQL injection vulnerability.
**Learning:** Even internal metadata or extracted file strings (like `dataReferencia`) can potentially be manipulated or contain unexpected characters that lead to SQL injection when interpolated directly.
**Prevention:** Always use parameterized/bound SQL queries with SQLAlchemy's `text()` and pass variables as bind parameters rather than using f-string interpolation.
