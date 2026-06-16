# Sentinel's Journal - CNPJ MySQL/Postgres Ingestion Pipeline

## 2024-05-22 - [Initial Security Audit]
**Vulnerability:** Hardcoded database credentials and SQL injection risk in `_referencia` table insertion.
**Learning:** The ingestion scripts used hardcoded default credentials and string formatting (f-strings) for SQL queries, which is a common pattern in scripts not intended for production but poses a risk if deployed or used with untrusted data.
**Prevention:** Always use environment variables for sensitive configuration and parameterized queries for all SQL operations.
