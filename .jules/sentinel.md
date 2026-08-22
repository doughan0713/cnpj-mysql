## 2026-03-31 - Fix SQL Injection in Metadata Table Ingestion
**Vulnerability:** Raw f-string interpolation was used when executing SQL `INSERT` statements into the `_referencia` metadata table (`dados_cnpj_mysql.py` and `dados_cnpj_postgres.py`).
**Learning:** `sqlalchemy.text()` strings containing python f-string expressions are evaluated prior to database execution, bypassing parameterization if dynamic variables are embedded directly in the string.
**Prevention:** Always pass variables into SQL query parameters using named bind variables (e.g. `:val`) and a dictionary of parameters to `engine.execute(text(...), params)`.
