## 2026-06-25 - Hardcoded Database Credentials and SQL Injection
**Vulnerability:** Database credentials (username, password, host, dbname) were hardcoded in the ingestion scripts. Additionally, metadata tables like `_referencia` were populated using f-string interpolation, creating a potential SQL injection risk if variables like `dataReferencia` were sourced from untrusted inputs.
**Learning:** Legacy scripts often prioritize ease of setup by hardcoding defaults, which can lead to accidental exposure of credentials in shared environments.
**Prevention:** Always use environment variables for sensitive configuration and prefer parameterized queries even for internal metadata updates.
