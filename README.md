# ASF Digital Solutions CRM

Streamlit CRM with Dashboard, Add Lead, Manage Leads, WhatsApp click-to-chat, CSV/Excel import/export, and Setup Guide. Styling is in `style.css` (black, deep navy, gold, white).

## 1. Run locally

```bash
python -m venv .venv
# Windows:
.venv\\Scripts\\activate
pip install -r requirements.txt
```

Copy `.streamlit/secrets.toml.example` to `.streamlit/secrets.toml` and enter your credentials. Then:

```bash
streamlit run app.py
```

## 2. Supabase setup

For a **new** Supabase project, open SQL Editor and run `supabase_schema.sql`. If you already have a `leads` table, do not blindly recreate it; compare its columns with the schema and preserve existing data.

Use the project URL and a suitable key in `.streamlit/secrets.toml`. Do not commit that file to GitHub. Do not expose a `service_role` or secret key in a public repository. If using an anon/publishable key, configure proper Row Level Security policies.

## 3. GitHub upload

Upload the project files, but **do not upload `.streamlit/secrets.toml`**. `.gitignore` excludes it. Keep `app.py`, `style.css`, `requirements.txt`, `README.md`, and `supabase_schema.sql` in the repository root.

## 4. Streamlit Community Cloud

Create/deploy the app from your GitHub repository. In app settings, add the following under Secrets:

```toml
SUPABASE_URL = "https://YOUR-PROJECT-REF.supabase.co"
SUPABASE_KEY = "YOUR-KEY"
APP_PASSWORD = "YOUR-STRONG-PASSWORD"
```

Save and reboot the app.

## WhatsApp

The app creates a WhatsApp click-to-chat link using the entered lead phone number and opens a prefilled message for the user to review and send. It does not send messages automatically. Phone numbers should include country code or use a Pakistan mobile number format.

## Logo

Place the original company logo in the project root using one of these names: `asf_logo.jpg`, `asf-logo-original.jpg`, `asf_logo.png`, `asf-logo-original.png`, or `logo.png`. The app uses the provided logo file unchanged.
