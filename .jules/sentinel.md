## 2026-06-15 - Parameterized Metadata Insertions

**Vulnerability:** SQL Injection vulnerability where `_referencia` metadata table insertions used f-string variable interpolation (e.g., `f"insert into _referencia (referencia, valor) values ('CNPJ', '{dataReferencia}')"`).

**Learning:** Unsanitized variables like `dataReferencia` or `qtde_cnpjs` constructed from dynamic sources/file names could allow SQL injection if manipulated.

**Prevention:** Always use SQLAlchemy `text()` parameterized queries with dictionary bind parameters (e.g., `text("insert into ... values (:referencia, :valor)"), {"referencia": ..., "valor": ...}`) rather than f-string interpolation when executing dynamic queries.
