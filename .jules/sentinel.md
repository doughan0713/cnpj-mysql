## 2026-06-15 - SQL Injection in _referencia Ingestion SQL
**Vulnerability:** Ingestion scripts populated the metadata table `_referencia` using Python f-string interpolation for variables like `dataReferencia` and `qtde_cnpjs`, allowing SQL injection if data inputs were manipulated.
**Learning:** Raw f-strings should never be used to construct SQL queries, even for values derived from file parsing, as any external context control could lead to full database compromise.
**Prevention:** Use SQLAlchemy parameterized `text()` queries and pass values via bind parameter dictionaries.
