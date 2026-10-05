# OAUHub

Play at https://reni0900.github.io/oauhub/.

An OAU campus life game with student accounts, customizable avatars, hostel activities, a phone and multiplayer.

## Hosting

GitHub Pages serves the static frontend from the main branch root. The Cloudflare Free Worker at https://oauhub-api.reniboyyy.workers.dev connects it to the existing OAU Life API and database. Existing accounts and saved progress stay in that database. This deployment still depends on the original Site backend remaining online; it does not migrate the database to Cloudflare.

The gateway accepts game requests only from https://reni0900.github.io and forwards only the three fixed game API routes. Login sessions are stored in the browser tab and closing it may require signing in again. No player records, passwords or session tokens are included in this repository.

## Updating

The source backup is oauhub-github.zip. Extract it, run npm ci --legacy-peer-deps, set OAUHUB_API_URL=https://oauhub-api.reniboyyy.workers.dev and run node scripts/build-oauhub.mjs. Upload the resulting dist/pages files to the repository root. Changes to the original Site do not automatically update this frontend.

The gateway source is hosting/worker.ts in the backup. Deploy its compiled JavaScript using Cloudflare Workers. No paid plan or purchased domain is needed for these addresses.
