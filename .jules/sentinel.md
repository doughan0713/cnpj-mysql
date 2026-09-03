## 2026-06-30 - Parameterized Insertions in _referencia Metadata Table
**Vulnerability:** Raw f-string SQL queries were used when inserting `dataReferencia` and `qtde_cnpjs` values into the `_referencia` metadata table in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`.
**Learning:** SQL insertions constructed using f-string interpolation rather than SQLAlchemy bind parameters create SQL injection risks if variables contain untrusted or unescaped data.
**Prevention:** Always use SQLAlchemy `text()` with bind parameter dictionaries (e.g., `engine.execute(text("..."), {"ref": ..., "val": ...})`) when performing SQL INSERT statements.
