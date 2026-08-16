## 2026-08-16 - Parameterized Queries for Metadata Insertions
**Vulnerability:** SQL Injection in metadata insertions using f-string interpolation for variables `dataReferencia` and `qtde_cnpjs`.
**Learning:** Raw string interpolation in `text(...)` queries bypasses database driver escaping.
**Prevention:** Always use parameterized queries with SQLAlchemy `text(...)` and parameter dictionaries (e.g. `{"dataReferencia": str(...)}`).
