# Running AI-PDF-Reader

## Local development

Use Node.js 22 or newer (Node.js 24 was used during recovery). Use the package manager matching the committed lockfile.

```powershell
npm ci
# Only if .env.local does not already exist:
# Copy-Item .env.example .env.local
# Fill the blank values in .env.local using your service dashboards.
npm run check:env
npm run dev
```

Open http://localhost:3000. To run several projects, give each a separate port, for example `npm run dev -- -p 3001`.

`.env.local` is present in the recovered working folder. `.env.example` is committed to GitHub; real environment values stay local. Blank values mean they have not yet been recovered. Do not replace an existing local file with the template.

`check:env` checks that required values are present without printing them. It does not validate credentials, database contents, account access or subscriptions. A successful build also does not prove that external services work.

## Verification

```powershell
npm run build
npm run start
```

For a type check without contacting services, run `npm run typecheck`.

## Service setup

Use the API keys from the original Clerk application, or create a replacement Clerk application and add both keys to `.env.local`. Existing users belong to the old Clerk application.

Routes: `/`, `/dashboard`, `/dashboard/upload`.

This checkout contains the landing page, authentication and an upload UI. The file-drop handler currently only logs files; PDF storage, parsing and AI answers have not been implemented in this version.
