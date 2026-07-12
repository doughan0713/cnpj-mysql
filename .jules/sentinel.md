## 2025-05-15 - SQL Injection in _referencia table
**Vulnerability:** Use of f-strings to interpolate variables into SQL queries for the `_referencia` table.
**Learning:** Metadata tables like `_referencia` were populated using f-string interpolation, creating a risk if the input data (e.g., `dataReferencia`) could be manipulated.
**Prevention:** Always use parameterized queries (bind parameters) for SQL execution, even for seemingly "safe" internal metadata.
