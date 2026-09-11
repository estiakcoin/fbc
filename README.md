# Kulanandapur Fantastic FC — Club Management Web App

Next.js + PostgreSQL (Drizzle ORM) project for the club's public website, member portal, and admin panel.

## ⚠️ How to upload this to GitHub (read this first)

**Do not zip and re-upload this folder as-is.** When you extract this project, your phone/computer's
unzip app usually creates a wrapping folder (e.g. `football-club-management-system-fixed/`). If you
upload *that folder* to GitHub, all your files end up one level too deep, and Vercel/Netlify will fail
with an error like `Couldn't find any 'pages' or 'app' directory`.

**Correct way:**
1. Extract this zip.
2. Open the extracted folder — you should see `package.json`, `src/`, `next.config.ts`, etc. directly inside it.
3. On GitHub, go to your repo → **Add file → Upload files**.
4. Select **all the items inside** that folder (not the folder itself) and drag them in.
5. Commit.

Your repo's root should show `package.json` directly — not `some-folder/package.json`.

**Safety net:** if this still goes wrong, go to your Vercel project → **Settings → General → Root Directory**,
and set it to whatever subfolder your files ended up in. That also fixes it without re-uploading anything.

## Local development

```bash
npm install
cp .env.example .env   # then fill in real values
npx drizzle-kit push   # creates/updates database tables
npm run dev
```

## Environment variables

See `.env.example`. You need at minimum:
- `DATABASE_URL` — a PostgreSQL connection string (e.g. from [Neon](https://neon.tech), free tier)
- `RESEND_API_KEY` — for sending emails (contact form, PIN resets, news notifications). Without it, the app still works, it just skips sending email.
- `ADMIN_EMAIL_FROM` — the "from" address used in outgoing emails

## Deploying

- **Vercel**: Import the GitHub repo at vercel.com/new, add the environment variables above, deploy.
- **Netlify**: Already configured via `netlify.toml` — import the GitHub repo at app.netlify.com, add the same environment variables, deploy.

After the first deploy (or whenever the schema changes), run `npx drizzle-kit push` with your production
`DATABASE_URL` to create/update the database tables.
