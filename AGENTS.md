# AGENTS.md

## Sadr

### Build and test
- The repo has no tests and no build step. The check is that the inline script in index.html parses and the page serves.
- Extract the one `<script>` block of index.html to a file and run `node --check FILE`. It passes with no output.
- Run `python3 -m http.server 8765 --bind 127.0.0.1` at the repo root, request `http://127.0.0.1:8765/`, and expect HTTP 200. Then stop the server.

### Toolchain
- The repo has no package manager, no lockfile and no runtime pin. The site is the single file index.html with inline CSS and JavaScript, and it loads no external resources.

### Deploys outside CI
- None. .github/workflows/static.yaml deploys the whole repo root to GitHub Pages on every push to main, so every file in the root is public on the site.

### Security notes
- Semgrep scans index.html with HTML rules only. It does not parse the inline `<script>` block as JavaScript, so no JavaScript rule covers the site's code.
