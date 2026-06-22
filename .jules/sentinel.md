## 2026-06-23 - [SQL Injection in Metadata via Untrusted Filenames]
**Vulnerability:** SQL Injection in the `_referencia` table during data ingestion.
**Learning:** The application extracted metadata (like dates) from filenames and inserted them into a database table using f-strings. This allowed an attacker with control over the source files to execute arbitrary SQL by crafting a malicious filename.
**Prevention:** Always use parameterized queries (bind parameters) with SQLAlchemy's `text()` function, even for metadata that seems internal. Never use string interpolation for SQL values.

## 2026-06-23 - [Hardcoded Credentials and Secret Exposure]
**Vulnerability:** Hardcoded database credentials in ingestion scripts and lack of `.gitignore`.
**Learning:** Ingestion scripts contained default usernames and passwords, and the repository lacked a `.gitignore`, risking the accidental commit of `.env` files or local database artifacts.
**Prevention:** Use a lightweight `.env` loader and `os.getenv()` for all sensitive configuration. Provide a `.env.example` template and explicitly ignore `.env` and platform-specific artifacts like `__pycache__` in `.gitignore`.
