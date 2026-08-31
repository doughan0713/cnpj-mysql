## 2026-03-30 - Parameterize Metadata Table Insertion Queries
**Vulnerability:** SQL injection risk in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` due to f-string interpolation when inserting reference metadata into the `_referencia` table.
**Learning:** `text(f"insert into _referencia ... '{dataReferencia}'")` passes raw unescaped strings directly to SQL execution.
**Prevention:** Always use SQLAlchemy `text()` parameterized queries with bind parameters (e.g. `:dataReferencia`) and a parameter dictionary instead of string formatting.
