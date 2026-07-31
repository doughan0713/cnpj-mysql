# Sentinel Security Journal

## 2026-07-31 - SQL Injection in Metadata Table Insertions
**Vulnerability:** Ingestion scripts used f-string SQL query formatting (e.g. `engine.execute(text(f"insert into _referencia ..."))`) with variables parsed from data files or runtime inputs, leading to potential SQL injection vulnerability.
**Learning:** Even metadata and logging table insertions must be fully parameterized. Direct interpolation using f-strings inside SQLAlchemy `text()` wrappers is a common bypass for ORM parameterization.
**Prevention:** Always use parameterized queries with named bind parameters and pass argument dicts to SQLAlchemy `Connection.execute()`.

## 2026-07-31 - Hardcoded Database Credentials and Insecure Connection URLs
**Vulnerability:** Database connection strings and login credentials (passwords, usernames) were hardcoded directly in Python scripts and formatted using unvalidated string formatting, raising risks of secret exposure and injection attacks via credentials.
**Learning:** Storing secrets in source files violates security principles and can lead to accidental leaks. Parsing `.env` files with a lightweight custom loader and building URLs via SQLAlchemy `URL.create` secures special character handling and isolates credentials.
**Prevention:** Provide a safe, zero-dependency environment variable parser (`carregar_env`), validate port types using `str.isdigit()`, and construct database URLs using `sqlalchemy.engine.URL.create`.
