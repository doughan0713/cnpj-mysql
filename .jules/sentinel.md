## 2026-07-28 - Secure SQL Insertion for Metadata Tables
**Vulnerability:** SQL injection risks due to string interpolation (f-strings) in metadata tables insertion (specifically `_referencia` insertions).
**Learning:** In metadata insertion steps, f-strings were used to dynamically interpolate values like `dataReferencia` into raw SQL insert queries. While seemingly harmless if variables are sourced locally, they still pose a SQL injection risk if the source files/metadata are manipulated.
**Prevention:** Always parameterize SQL insert queries using SQLAlchemy `text()` and bind parameters (`:param_name`), passing arguments as a dictionary.
