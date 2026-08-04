## 2026-08-04 - SQL Injection in Metadata Insertion

**Vulnerability:**
The metadata table `_referencia` was populated with the database date and count reference using raw python f-string interpolation: `text(f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')")` and `text(f"insert into _referencia (referencia, valor) values ('cnpj_qtde', '{qtde_cnpjs}')")`. Since raw user input and scraped file metadata values are inserted, this could be exploited via SQL injection.

**Learning:**
Even helper metadata tables, utility queries, or backend admin insertions are susceptible to SQL injection if f-string concatenation or string formatting is used with SQL queries. Passing `text(...)` alone does not make a query safe; variables must be explicitly parameterized using query bindings.

**Prevention:**
Always parameterize all dynamic values in SQL queries using SQLAlchemy's bind parameter syntax (e.g. `:variable_name`) and supply parameters as a dictionary in `engine.execute(text(sql), {"variable_name": value})`.
