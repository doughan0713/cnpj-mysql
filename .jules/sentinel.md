## 2025-05-22 - Hardcoded Credentials and SQL Injection in Ingestion Scripts
**Vulnerability:** Database credentials (username, password) were hardcoded in the ingestion scripts. Additionally, metadata about the ingestion process was being inserted into the `_referencia` table using f-strings, posing a SQL injection risk if the source data or reference dates were manipulated.
**Learning:** Legacy data processing scripts often prioritize ease of use (copy-paste configuration) over security, leading to secrets being committed to version control.
**Prevention:** Use environment variables for all sensitive configuration and always use parameterized queries for SQL operations, even for internal metadata.
