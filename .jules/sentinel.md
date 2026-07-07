# Sentinel Security Journal

## 2025-05-14 - Hardcoded Credentials and SQL Injection
**Vulnerability:** Database credentials (username, password, host, dbname) were hardcoded in the ingestion scripts. Additionally, data insertion into the `_referencia` table used f-strings, leading to SQL injection risks.
**Learning:** Legacy scripts often prioritize ease of use over security, leading to hardcoded secrets and unsafe query construction.
**Prevention:** Always use environment variables for sensitive configuration and use parameterized queries for all SQL operations.
