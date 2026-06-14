## 2026-06-14 - Credential Management and SQL Injection Prevention
**Vulnerability:** Hardcoded database credentials and string-formatted SQL queries for data insertion.
**Learning:** Legacy scripts often use hardcoded values for simplicity, which poses a risk when shared or deployed. String-formatted queries for `INSERT` statements, even when using well-known values like record counts, are a potential injection vector if the source data is ever compromised.
**Prevention:** Always use `os.getenv` for configurations and leverage SQLAlchemy's `text()` with bind parameters for ALL SQL operations.
