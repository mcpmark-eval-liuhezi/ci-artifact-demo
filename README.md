# ci-artifact-demo

This repository is a **workshop demo**. It exists so a team can be walked through,
end to end, how a GitHub Actions pipeline publishes build artifacts and a release.

## What the demo shows

The [Artifact Audit](.github/workflows/audit.yml) workflow is started manually
(`workflow_dispatch`). When it runs, it:

1. writes a short text audit report,
2. uploads that report as a GitHub Actions **artifact** named `audit-report`,
3. publishes a GitHub **release** tagged `v0.1.0` that carries the same report.

## How to run it

- In the UI: **Actions → Artifact Audit → Run workflow** (pick the default branch), or from a terminal:

  ```
  gh workflow run audit.yml --ref main
  ```

- When the run is green, open the run summary page to download the `audit-report`
  artifact, and check the repository's **Releases** page for the `v0.1.0` release.

Everything in this repository is for demonstration purposes only.
