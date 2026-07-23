## 2026-06-25 - SQL Injection Vulnerability in Reference Metadata Ingestion
**Vulnerability:** SQL injection vulnerability when inserting public data metadata into the `_referencia` table of the database in both `dados_cnpj_mysql.py` and `dados_cnpj_postgres.py` via f-string string interpolation.
**Learning:** Raw string formatting of dynamically populated metrics or data (like `dataReferencia` or `qtde_cnpjs`) bypassing the proper SQL parser and allowing potential query manipulation or execution of malicious commands during database schema preparation.
**Prevention:** Always use parameterized SQL statements utilizing bind parameters (e.g., SQLAlchemy's `text("...")` with a parameters dictionary) to execute insert statements instead of string formatting or string interpolation.
