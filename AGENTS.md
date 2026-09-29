# Base44 Dev Environment

## Project
A single-page static birthday site (`index.html` + `audio/`, `fonts/`, `img/` assets). No backend, no build step, no dependencies, no secrets.

## Running
- `docker compose -f docker-compose.base44.yml up -d`
- nginx (alpine) serves the repo root (bind-mounted read-only) on host port 3000.
- `nginx.base44.conf` runs the worker as `root` because the sandbox repo dir is `700 root` (nginx's default `nginx` worker user would 403).

## Editing
- Edits to `index.html` and assets are served live from the bind mount — refresh the browser (or call `reload_preview`) to see them. There is no HMR/build step.

## Verifying
- `curl -s -o /dev/null -w "%{http_code}\n" http://localhost:3000/` → 200
- Check assets: `/img/logo-ec-gold.png`, `/audio/tropicoqueta-90s.mp3`
