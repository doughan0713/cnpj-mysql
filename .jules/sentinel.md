## 2026-06-15 - [Hardcoded Credentials and Insecure Connection Strings]
**Vulnerability:** Database credentials (user, password) were hardcoded in the ingestion scripts, and connection URLs were built using f-strings.
**Learning:** Hardcoding credentials is a major security risk as they can be easily exposed. Using f-strings for URL construction doesn't properly escape special characters in passwords.
**Prevention:** Use environment variables for sensitive configuration and SQLAlchemy's `URL.create` for secure connection string building.
