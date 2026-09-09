## 2026-06-01 - SQL Injection in Metadata Table Population
**Vulnerability:** String formatting (f-strings) was used in raw SQL INSERT statements when inserting reference data (`dataReferencia` and `qtde_cnpjs`) into the `_referencia` metadata table.
**Learning:** Even internal metadata variables derived from file name parsing or query counts can pose SQL injection risks or cause syntax errors if untrusted file metadata contains SQL special characters.
**Prevention:** Always use parameterized SQL queries with SQLAlchemy `text()` and bind parameter dictionaries (`{"param": val}`) for values in DML statements.
