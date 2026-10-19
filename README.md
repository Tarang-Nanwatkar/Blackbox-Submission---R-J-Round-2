# Blackbox — Complete Project

This single archive combines the current web application with the exact published Python research release. There are no nested ZIP files.

## Contents

- `frontend/`: complete browser UI, backend APIs, conservative JavaScript matching engine, local/durable-storage adapters, tests, all 480 historical case details, and Vercel configuration. The backend is included in this directory under `api/`, `server/`, and `lib/`.
- `research_release/`: original Python inference interface, training scripts, trained model assets, organiser kit/data, baselines, ablations, frozen experiments, results, technical report, verification tools, Dockerfiles and compiled CPython 3.12 assets. Every original file is preserved unchanged.
- `PROJECT_OVERVIEW.md`: the 1,000-word project overview.
- `BUNDLE_MANIFEST.json`: file inventory, hashes and provenance for this combined distribution.

The frontend source corresponds to GitHub commit `f6bbf2802e513ffff209c951c5d9015b4f4c7307`. The research source is extracted from the published archive whose SHA-256 is `c03ae58397104e276a67d7d343e8be4635a499352111c24e1e774d0ea9dee936`. This combined ZIP has its own identity; it is not a replacement for that frozen submission artifact.

## Run the full application

Use Node.js 24. Open a terminal inside `frontend/`:

```bash
npm ci
npm run dev
```

Open `http://localhost:3000`. The development command builds the static assets and starts the backend together. Local sessions use SQLite under `.runtime/`. No external database credentials are needed for local development. The complete test suite also needs a `python3` command; WSL2 provides a suitable environment for Windows users.

## Run the Python policy

Use CPython 3.12; the retained reference version is 3.12.14. From `research_release/`:

```bash
python3.12 -S -B policy.py --mode conservative < runtime/examples/refreshed_match_request.json
```

Windows CMD:

```bat
py -3.12 -S -B policy.py --mode conservative < runtime\examples\refreshed_match_request.json
```

For training, reproduction and verification, follow `research_release/README.md` and `research_release/TECHNICAL_REPORT.md`. Python inference and the web application are separate implementations. Live JavaScript simulations are not official Python benchmark results. Learned models remain experimental; conservative is active.

## Deployment status

The existing private Sites application is live at https://blackbox-match-lab.jwalith4418.chatgpt.site/. Its original Worker/D1 implementation is managed separately.

The included Vercel target is prepared but not deployed. Workspace access was denied with HTTP 403, and no authorized Vercel workspaces were returned on the later check. Grant the connection access to `jwalith4418-2769s-projects`, configure `TURSO_DATABASE_URL` and `TURSO_AUTH_TOKEN` using Vercel's protected settings, and set Root Directory to `frontend`. Keep Vercel Authentication enabled for all deployments. Follow `frontend/README.md` for the verification steps.

No API keys, installed dependencies, temporary databases, build caches, previous-version ZIPs or nested submission archives are included. Native Windows and constrained Docker certification of the research release, remote Vercel/database verification, and browser visual QA remain unverified. Historical status fields inside the frozen research release describe their authoring time; the current application publication status is recorded here.
