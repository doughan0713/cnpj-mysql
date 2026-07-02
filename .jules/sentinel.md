# Sentinel Journal - CNPJ Ingestion Security

## 2026-06-15 - [Credential Exposure]
**Vulnerability:** Hardcoded database credentials (username, password, host, dbname) in ingestion scripts.
**Learning:** Initial development scripts often use hardcoded values for convenience, which can be accidentally committed.
**Prevention:** Always use environment variables and provide a `.env.example` template.

## 2026-06-15 - [SQL Injection]
**Vulnerability:** Use of f-strings for SQL query construction in `engine.execute(text(f"..."))`.
**Learning:** Even internal scripts can be vulnerable if input sources change or if they are adapted for multi-user environments.
**Prevention:** Use SQLAlchemy's `text()` with bind parameters for all dynamic SQL.

## 2026-06-15 - [Information Disclosure]
**Vulnerability:** Data directories and `.env` files not excluded from version control.
**Learning:** Missing `.gitignore` leads to accidental leakage of large datasets and sensitive configuration.
**Prevention:** Maintain a robust `.gitignore` file.
