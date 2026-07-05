## 2025-05-15 - [Secure Database Connection String Construction]
**Vulnerability:** Hardcoded database credentials and insecure connection string construction using f-strings.
**Learning:** Hardcoding credentials makes them susceptible to exposure via version control. Constructing SQLAlchemy URLs via f-strings (e.g., `f"mysql://{user}:{pass}@{host}/{db}"`) is dangerous if credentials contain special characters that aren't URL-encoded, potentially leading to connection failures or injection-like issues.
**Prevention:** Use environment variables for all sensitive configuration. Utilize `sqlalchemy.engine.URL.create` which automatically handles the necessary encoding and formatting for various database drivers, ensuring a secure and robust connection string.
