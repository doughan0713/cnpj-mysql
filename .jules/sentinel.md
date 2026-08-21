## 2026-06-30 - SQL Injection in Metadata Table Ingestion
**Vulnerability:** Raw f-string interpolation in `engine.execute(text(f"insert into _referencia ..."))` statements in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` allowed potential SQL injection via metadata variables.
**Learning:** SQL queries built via f-strings are vulnerable even when wrapped in SQLAlchemy `text()`.
**Prevention:** Always use SQLAlchemy bind parameter dictionaries with `text()` for parameterized SQL execution.
