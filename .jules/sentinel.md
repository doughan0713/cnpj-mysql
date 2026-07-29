## 2026-06-15 - Parameterized SQL Queries in Metadata Ingestion
**Vulnerability:** The data ingestion pipeline used string formatting (f-strings) to populate metadata tables like `_referencia` with `dataReferencia` and `qtde_cnpjs`. This introduced potential SQL injection risks if the source files or file names contained malicious inputs designed to escape the insert statement.
**Learning:** Dynamically constructed query strings, even for internal run stats or dates extracted from file naming schemas, should never be interpolated directly.
**Prevention:** Always use parameterized SQL execution (via SQLAlchemy's `text` and bind parameter dictionary) to separate query instructions from user-controlled/external data inputs.
