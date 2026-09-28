# FMS WebCarrot demo handover

## Source and policy

- Demo repository: `fullmetalsonic/webcarrot-offline-demo-fms` (separate from the official-source demo).
- Settings source: `fullmetalsonic/openpilot:fms-carrot-wip` at `0a3d206b9b89eafe3d502b9ba5e596e89ad7885a`.
- Do not automatically follow `ajouatom/openpilot:carrot-wip`, the existing official-source demo, or future FMS changes. Update this demo only on the owner's explicit request.
- Source schema is embedded from `openpilot/selfdrive/carrot_settings.json` at the exact source commit. It has 184 settings, 4 top-level menu categories, and the unpatched `DisableDM` entry.
- Relative to the official-source demo v1.0.5, this source changes only `PaddleMode` and `VEgoStopping` fields. The menu tree and parameter keys are unchanged. Existing vehicle names are retained because vehicle definition files did not change in the source comparison.

## Delivery

- `index.html` is the standalone offline app and the Pages root.
- Release asset `webcarrot-offline-demo-fms.html` must be byte-identical to `index.html`.
- App version starts at `1.0.0`, independently of the official-source demo. The in-app update check points only to the FMS repository.
- Published v1.0.0 at `https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/tag/v1.0.0`; Pages is `https://fullmetalsonic.github.io/webcarrot-offline-demo-fms/`.
- At publication, Pages and the Release HTML both returned HTTP 200 and matched local `index.html` byte for byte (SHA-256 `26a5c2a7a313502e3b20e57a98bcc74424b5d27f94c7c5bf2637a9e528492890`). The latest stable Release API returned v1.0.0 with CORS `*`.
- Preserve unknown imported keys and unedited JSON values/types. Parameter count must never cause deletion or migration of backup data.
- Before a requested update, check the live FMS branch HEAD and compare complete menu order, group hierarchy, labels, descriptions, controls, bounds, defaults, choices, vehicle conditions and catalog. Record the source SHA and increment the app version only for an actual demo change.
- Before publishing, check public files for private data and verify schema/source equality, HTML JavaScript syntax, changed-file whitespace, Pages response and Release asset parity. Do not call rendered or phone behavior verified without observing it.

## Limits

- This demo does not contact a Comma device. Online update checks query only public GitHub Release metadata.
- The original demo's local uncommitted v1.0.6 driver monitoring work was not copied into this repository.
- No automatic schedule belongs to this FMS demo.
- JavaScript syntax, exact source schema equality, Git whitespace, and publication parity were checked. Rendered UI and physical phone behavior were not checked in this delivery.
