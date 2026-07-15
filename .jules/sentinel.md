## 2026-06-18 - SQL Injection in Metadata Tables
**Vulnerability:** Metadata tables like `_referencia` were populated using f-string interpolation for values like `dataReferencia`, creating a potential SQL injection risk if source data or user-provided reference dates were malicious.
**Learning:** Even internal metadata tables often bypass strict parameterization because they are seen as "low risk" or "one-off" operations.
**Prevention:** Always use parameterized queries with `sqlalchemy.text()` and bind parameter dictionaries for all SQL insertions, regardless of the perceived sensitivity of the table.

## 2026-06-18 - Insecure Credential Handling
**Vulnerability:** Database credentials (username, password, host) were hardcoded in scripts or manually edited by users, increasing the risk of accidental exposure in version control.
**Learning:** Lack of a standard environment variable loading mechanism forces users to modify source code to configure the application.
**Prevention:** Use a `.env` file and a dedicated loader function to inject credentials into `os.environ`, and use `URL.create` from SQLAlchemy to build connection strings safely.
