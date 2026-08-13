## 2026-06-25 - SQL Injection via f-strings inside SQLAlchemy text()
**Vulnerability:** Inserting unvalidated data into the metadata table `_referencia` using Python f-string interpolation inside `text()` clauses created a risk of SQL Injection.
**Learning:** This vulnerability existed because metadata variables like `dataReferencia` and `qtde_cnpjs` were dynamically constructed and directly interpolated into the SQL string. Although the context here was metadata, SQL interpolation remains an insecure practice.
**Prevention:** Always use parameterized query placeholders (e.g. `:variable`) in SQLAlchemy `text()` clauses and supply a dict with bind parameters to `engine.execute()`. This securely separates the query syntax from the data.
