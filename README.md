# AR Digital Creates — Vercel Version

This version is structured for GitHub + Vercel.

## Important

Upload the **contents of this folder** to the root of your GitHub repository. The repository should contain `index.html`, `app.js`, `styles.css`, `api/`, `admin/`, `database/`, `package.json`, and `vercel.json` at the top level.

## Vercel deployment

1. Import the GitHub repository into Vercel.
2. Framework Preset: Other (or let Vercel detect the static site).
3. Build Command: leave empty.
4. Output Directory: leave empty.
5. Deploy.

The project does not pin a per-function runtime in `vercel.json`. Vercel will use the Node.js version configured for the project/package. The package targets Node.js 24.x.

## Database

Create a PostgreSQL database (for example Neon) and set:

`DATABASE_URL`

Run `database/schema.sql` against the database once.

## Admin

Set these Vercel Environment Variables:

`ADMIN_USERNAME`

`ADMIN_PASSWORD`

The admin page is `/admin/` and uses HTTP Basic Authentication for the API requests.

## Media uploads

Create/connect a Vercel Blob store so Vercel provides:

`BLOB_READ_WRITE_TOKEN`

The current server upload route limits individual uploads to 4 MB to stay below Vercel Function request limits. Larger media can be added later with a direct client-upload flow.

## API routes

- `POST /api/enquiries`
- `GET /api/assets`
- `GET /api/admin/session`
- `GET /api/admin/enquiries`
- `GET /api/admin/assets-list`
- `POST /api/admin/assets`

## Troubleshooting

If Vercel reports `Function Runtimes must have a valid version`, make sure you are deploying this corrected version and that an old `vercel.json` or `now.json` is not also present in the repository. The corrected `vercel.json` intentionally does not contain a `functions.runtime` entry.
