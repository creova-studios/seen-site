# Security Policy (`SECURITY.md`)

## Scope

`creova-studios/seen-site` hosts the pre-built static HTML/CSS/JS production web artifact served via GitHub Pages at **`https://seen.creova.one`**. Upstream source code and build tooling live in [`creova-studios/seen`](https://github.com/creova-studios/seen) (`site/`).

## Enforced Static Security Posture

Every published HTML route (`EN`, `FR`, `ES` across `/`, `/terms/`, and `/privacy/`) enforces a strict zero-trust `Content-Security-Policy` meta policy and origin referrer boundary:

```text
Content-Security-Policy: default-src 'none'; script-src 'self'; style-src 'self'; font-src 'self'; img-src 'self' data:; base-uri 'self'; form-action 'none'
referrer="strict-origin-when-cross-origin"
```

- **Zero External Network Calls:** `connect-src`, `frame-src`, and third-party origins fall back to `default-src 'none'`. No analytics beacons, external fonts, or third-party scripts can execute.
- **Zero Client Persistence:** `site.js` is a self-contained 51-line Progressive Enhancement script for the interactive story-seed preview; it never reads or writes `document.cookie`, `localStorage`, or `sessionStorage`.
- **Automated CI Verification:** `.github/workflows/ci.yml` verifies CSP presence, asset integrity, `CNAME` alignment, and absence of external URLs or inline event handlers on every pull request and push to `main`.

## Reporting a Vulnerability

Do **not** open a public GitHub issue for security vulnerabilities. Report security issues via GitHub Private Vulnerability Reporting on [`creova-studios/seen`](https://github.com/creova-studios/seen) or email **`security@creova.one`**.

We acknowledge reports within **48 hours** and provide remediation timelines within **7 days**.
