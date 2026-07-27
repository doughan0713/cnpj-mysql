# Sentinel Security Journal

## 2026-06-16 - Parameterized Ingestion Metadata SQL Queries
**Vulnerability:** SQL Injection risk in metadata table insertions. The `_referencia` metadata table was populated using Python f-string SQL interpolation for variables `dataReferencia` and `qtde_cnpjs`, which can allow malicious database manipulation if those variables are derived from untrusted or user-supplied sources.
**Learning:** Legacy database ingestion scripts often use f-strings or string concatenation for simplicity, but when migrating to SQLAlchemy or modern DB libraries, passing raw formatted SQL string execution is an anti-pattern. Values must be parameterized even in seemingly minor metadata or reference insertions.
**Prevention:** Always use parameterized SQL placeholders (e.g., SQLAlchemy `:ref`, `:val`) and pass values via mapping/dictionary arguments in engine/connection executions.
