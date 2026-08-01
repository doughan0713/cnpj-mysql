## 2026-08-01 - Parameterized SQL Metadata Ingestion
**Vulnerability:** SQL Injection via string interpolation in metadata queries when storing base reference and count statistics into the `_referencia` table.
**Learning:** Historical ingestion scripts used f-strings to insert `dataReferencia` and `qtde_cnpjs` values into SQL commands, posing a risk of SQL injection if variables contained malicious inputs.
**Prevention:** Utilizing SQLAlchemy's parameterized execution with bind parameters ensures values are safely sanitized and quoted regardless of source.

## 2026-08-01 - Hardcoded Credentials and Driver Injection
**Vulnerability:** Hardcoded credentials and insecure connection string interpolation.
**Learning:** Hardcoding default database names, users, passwords, and hosts inside ingestion scripts risks credential leaks and exposes the database connection URL to parsing errors or injection if variables contain special characters (e.g., '@' or ':').
**Prevention:** Use environment variables loaded from a `.env` file via a secure custom parser, set default passwords to empty strings, and programmatically construct connection URLs using `sqlalchemy.engine.URL.create` with explicit driver specification and type-validated ports.
