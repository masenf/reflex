## v0.1.68 (2026-07-31)

### Features

- Added Google Cloud (GCP) as a managed deploy target for `reflex deploy`. When your organization has a GCP account connected (Enterprise tier), `reflex deploy` asks whether to deploy to Reflex Cloud or your GCP account (or pass `--provider gcp` / set `provider: gcp` in your config to skip the prompt), and `reflex cloud providers status` / `list` report the connection state.
- Added `reflex cloud apps rollback DEPLOYMENT_ID`, which rolls an app back to a previous deployment by redeploying its already-built image without rebuilding from source. `reflex cloud apps history` now reports whether each deployment can be rolled back to.
- Added optional per-deployment descriptions (changelog notes): set one at deploy time with `reflex deploy --description "..."`, set or clear it later with `reflex cloud apps describe`, and view it in `reflex cloud apps history`.


## v0.1.67 (2026-06-17)

### Features

- Added a `--service-account` flag to `reflex deploy --gcp`, letting Cloud Run services run as a least-privilege per-service service account instead of the project's default compute SA. ([#6556](https://github.com/reflex-dev/reflex/issues/6556))
- Added `--max-instances`, `--allow-unauthenticated/--no-allow-unauthenticated`, `--env KEY=VALUE`, and `--envfile` flags to `reflex deploy --gcp`, letting you cap Cloud Run autoscaling, deploy a private service, and set environment variables at deploy time. ([#6557](https://github.com/reflex-dev/reflex/issues/6557))
- Added `reflex cloud scan`, which uploads your app source for a Reflex-aware security review and reports security and logic flaws. Supports `--json` output and a `--fail-on` severity gate for CI. ([#6632](https://github.com/reflex-dev/reflex/issues/6632))
