# Christmas Gift Tracker — shared family edition

## Setup (desktop)

1. Create a free project at https://supabase.com/dashboard.
2. Open **SQL Editor** > **New query**. Paste the full contents of `schema.sql` and click **Run**. Run this only once on a new project.
3. Under **Project Settings > API** (sometimes **Connect** / **API Keys**), copy the **Project URL** and **publishable** key (or legacy **anon** key). Open `config.js` in Notepad and replace the two placeholders. **Never use a service_role or secret key in browser code.**
4. Under **Authentication > Providers > Email**, keep email/password enabled. Email confirmation is recommended. Under **Authentication > URL Configuration**, set Site URL to your published GitHub Pages address once known. Add that address to redirect URLs if needed.
5. Create a public GitHub repository named `christmas-gift-tracker` (GitHub Pages on free accounts generally requires a public repository). Upload `index.html`, `config.js`, `manifest.webmanifest`, `schema.sql`, and this README. The database is private because Supabase Row Level Security enforces access, **not** because the repository is private. Never commit passwords or secret/service-role keys.
6. In GitHub repository **Settings > Pages**, choose **Deploy from a branch**, branch **main**, folder **/(root)**, then **Save**. Wait for the Pages URL: `https://YOURUSERNAME.github.io/christmas-gift-tracker/`.
7. Open the site. Each adult creates a separate account and confirms email if prompted. One adult selects **Create family** and privately sends the invite code to the other; the other selects **Join existing family**.
8. On iPhone, open the site in Safari > Share > **Add to Home Screen**. On desktop, bookmark the URL. Both accounts can edit the same people and gifts. Updates normally arrive live via Supabase Realtime; refreshing the page also syncs.
9. Click **Export backup** periodically and save the JSON file to OneDrive. Backups can be reviewed manually; this edition does not include one-click restore/import.

## Important notes
- Supabase free-tier limits and inactivity policies can change. Check their current plan terms.
- Invite codes grant access to the whole family list; share privately. This edition has no invite-code rotation or member-removal UI.
- Gift status `planned` is excluded from spent totals. `purchased` and `wrapped` count as spending. Costs are estimates or amounts you enter, not linked to a bank.
- GitHub Pages is static hosting. The publishable key and project URL are intentionally visible; Supabase authentication and RLS protect the records.
- If realtime changes do not appear, confirm the `supabase_realtime` publication includes `people` and `gifts` in Supabase Database > Publications. Refreshing the page always fetches latest saved data.
- The first adult's family is selected if an account belongs to multiple families; this simple edition does not have a family switcher.
