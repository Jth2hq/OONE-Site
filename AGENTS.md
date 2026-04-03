# AGENTS.md

## Cursor Cloud specific instructions

### Project overview
OONE is a self-contained single-page portfolio/creative website. The entire application lives in `README.md`, which is an HTML document (with embedded CSS and vanilla JS). There is no build step, no package manager, no backend, and no local dependencies to install.

### Serving the application
The file must be served over HTTP (not `file://`) for `fetch()` calls and ES module imports to work. A symlink `index.html -> README.md` is used so Python's HTTP server sends the correct `text/html` MIME type:

```
ln -sf README.md index.html
python3 -m http.server 8080
```

Then open `http://localhost:8080/index.html` in a browser.

### Known issue: JavaScript syntax errors
The repository's JavaScript contains string literals that span multiple lines (newlines inside single-quoted strings), which causes `SyntaxError: Invalid or unexpected token` at runtime. This means all interactive JS features (navigation, canvas field, theme chooser, tutorial) are non-functional. The HTML structure and CSS styling render correctly. This is a **code issue in the repository**, not an environment problem.

### External dependencies (CDN-loaded, no local install needed)
- Google Fonts (Cormorant Garamond, Space Mono, IBM Plex Mono)
- `framer-motion@11` via `esm.sh` CDN
- Cosmos.so GraphQL API and Are.na API for feed content

### No lint/test/build tooling
There is no `package.json`, no test framework, no linter, and no build system configured in this repository.
