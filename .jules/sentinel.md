## 2026-06-15 - Hardcoded Credentials and SQL Injection
**Vulnerability:** Hardcoded database credentials (host, username, password) and potential SQL injection in metadata insertions via f-strings.
**Learning:** Legacy data ingestion scripts often prioritize ease of use (copy-paste config) over security, leading to credential leakage in source control.
**Prevention:** Always use environment variables for sensitive configuration and prefer parameterized queries over string interpolation, even for "internal" metadata.
