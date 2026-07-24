## 2026-06-15 - SQL Injection in Metadata Insertion
**Vulnerability:** SQL Injection in `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` via f-string interpolation during references insertion into the `_referencia` table.
**Learning:** Metadata tables were historically populated using simple f-string interpolation for variables like `dataReferencia` and `qtde_cnpjs`, which can lead to SQL injection.
**Prevention:** Use parameterized queries via SQLAlchemy's `text()` function with bind parameter dictionaries instead of string concatenation or interpolation.
