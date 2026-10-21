# Build notes — what this demo shows

This repo is a small, self-contained live demo for a workshop on **how GitHub Actions artifacts work end to end**.

## The end-to-end path

1. **Trigger** — the workflow in `.github/workflows/build-report.yml` runs on **every push to the `add-build-report` branch**.
2. **Build** — a deliberately trivial build step runs on `ubuntu-latest` (no real compilation, just echo output).
3. **Report** — the workflow writes a short plain-text report to `build-output/report.txt` inside the runner's workspace.
4. **Upload** — `actions/upload-artifact@v4` packages that file and uploads it as an artifact named **`build-report`**.
5. **Download** — the artifact is then downloadable from the workflow run's **Artifacts** section on the Actions tab (or via the API / `gh run download`).

## Things worth pointing out during the demo

- Only files inside the runner's workspace can be uploaded; anything the workflow needs to ship has to be written to disk first.
- The artifact **name** (`build-report`) is what you download by — the file keeps its own name (`report.txt`) inside the zip.
- Artifacts are scoped to a **workflow run**, and they expire (here: `retention-days: 30`).
- Because the trigger is scoped to this one branch, pushes to other branches do not produce artifacts.

## Where to look

- Workflow definition: `.github/workflows/build-report.yml`
- Generated report: uploaded as the `build-report` artifact on each run
- Related issue: "Publish a build-report artifact from CI"
