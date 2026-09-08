## 2026-03-30 - Parameterized SQL Query Bindings in Metadata Insertion
**Vulnerability:** SQL Injection in metadata insertion into `_referencia` table via f-string interpolation of `dataReferencia` and `qtde_cnpjs`.
**Learning:** Raw string interpolation into SQL queries creates SQL injection vulnerabilities even when variables are expected to hold non-user-supplied dates or integers.
**Prevention:** Always use parameterized SQL queries with SQLAlchemy `text()` and bind parameter dictionaries (`:referencia`, `:valor`) when executing queries.
