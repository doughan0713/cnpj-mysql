## 2026-06-21 - SQL Injection in Metadata Insertion
**Vulnerability:** SQL Injection via f-string interpolation during metadata table insertion in database ingestion scripts.
**Learning:** The variables `dataReferencia` and `qtde_cnpjs` were interpolated directly into raw SQL strings using Python f-strings, leading to possible SQL injection if the values were derived from external sources or manipulated.
**Prevention:** Use SQLAlchemy parameterized queries with `text()` and bind parameters (`{"key": value}`) to ensure all inputs are securely bound and sanitized.
