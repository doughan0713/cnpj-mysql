## 2024-11-20 - Parameterized Queries and Env Vars
**Vulnerability:** SQL injection in metadata insertion and hardcoded database credentials.
**Learning:** Even internal metadata insertions can be vulnerable if variables like `dataReferencia` (derived from file names) are not sanitized.
**Prevention:** Always use SQLAlchemy `text()` with bind parameters and avoid f-strings in SQL. Use environment variables for all credentials.
