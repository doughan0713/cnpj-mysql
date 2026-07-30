# Sentinel Journal

## 2026-06-15 - SQL Injection in Metadata Insertions
**Vulnerability:** SQL injection vulnerability via Python f-string interpolation when populating the database metadata table `_referencia` with `dataReferencia` and `qtde_cnpjs`.
**Learning:** The use of string formatting (f-strings) to construct SQL queries, even inside SQLAlchemy `text(...)`, bypasses SQL parameterization and database driver safety controls. If inputs are dynamically controlled, they could inject arbitrary SQL commands.
**Prevention:** Always use parameterized/prepared queries and bind parameters when passing dynamic variables to SQL execution methods.
