## 2024-06-30 - [Secure Database Ingestion Pattern]
**Vulnerability:** Hardcoded database credentials and potential SQL injection in ingestion scripts.
**Learning:** Legacy ingestion scripts often hardcode credentials for ease of use, and use string interpolation for SQL queries which can lead to SQL injection if data source is compromised.
**Prevention:** Always use environment variables (via a safe `.env` loader) for credentials and SQLAlchemy's `text()` with bind parameters for SQL execution. Use `URL.create` to safely handle special characters in connection strings.
