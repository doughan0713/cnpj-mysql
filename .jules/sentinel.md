# Sentinel Security Journal 🛡️

## 2026-06-12 - Secure Database Configuration and Parameterized Queries
**Vulnerability:** Hardcoded database credentials and SQL injection risk via string interpolation in metadata updates.
**Learning:** Ingestion scripts used hardcoded variables for database connection and string formatting for inserting metadata into the `_referencia` table.
**Prevention:** Use environment variables for credentials and SQLAlchemy `text()` with bind parameters for all SQL executions involving variable data.
