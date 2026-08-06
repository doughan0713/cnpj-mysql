## 2026-06-25 - Secure SQL insertions into the reference table
**Vulnerability:** SQL injection risks due to f-string/string interpolation of variables inside SQL queries execution under `_referencia` metadata tables creation.
**Learning:** Raw dynamic queries populated with local or external variables can lead to potential SQL injections if those parameters contain malicious content. Even metadata tables or internal parameters should always use parameterized queries.
**Prevention:** Use SQLAlchemy `text()` with bind parameter dictionaries and pass parameters separately to the database driver instead of using string interpolation.
