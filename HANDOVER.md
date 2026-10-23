# FMS WebCarrot demo handover

## Source and policy

- Demo repository: `fullmetalsonic/webcarrot-offline-demo-fms` (separate from the official-source demo).
- Settings source: `fullmetalsonic/openpilot:fms-carrot-wip` at `1b1e019ee6bf5778be751373f269ed4f5d874cf2`.
- Do not automatically follow `ajouatom/openpilot:carrot-wip`, the existing official-source demo, or future FMS changes. Update this demo only on the owner's explicit request.
- Source schema is embedded from `openpilot/selfdrive/carrot_settings.json` at the exact source commit. It has 193 settings, 4 top-level menu categories, and the existing `DisableDM` 0/1/2 entry.
- Relative to FMS demo v1.0.2, 12 keys were added, three YouTube keys removed, and 24 existing definitions changed. The menu contains new entries, with `ShareData` and `VehicleNaviDecelCancel` detail children and search-only `NNFF`. Three LongTuning settings are hidden for Hyundai/Toyota brands. Offline brand inference uses `CarSelected3` then `CarName` name prefixes; the device uses the fingerprinted brand first. Vehicle enum definitions did not gain names in the source range, so the catalog is retained.

## Delivery

- `index.html` is the standalone offline app and the Pages root.
- Release asset `webcarrot-offline-demo-fms.html` must be byte-identical to `index.html`.
- App version starts at `1.0.0`, independently of the official-source demo. The in-app update check points only to the FMS repository.
- v1.0.1 changes only search input behavior: keep the input DOM node while updating results, defer the first category-to-search transition during IME composition, and use one custom clear button. Embedded settings and source SHA remain unchanged.
- v1.0.2 adds search aliases for Korean steering spellings (스티어링/스테어링) because the source labels use 조향 and `Steer`. The embedded schema and source SHA remain unchanged.
- v1.0.3 embeds source SHA `1b1e019` and the updated settings definitions. The normal list omits detail children and search-only entries; the detail screen and search include them. It also corrects the FMS Pages origin path so hosted update can carry the current settings forward. No backup conversion or unsupported-key deletion was added.
- Published v1.0.2 at `https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/tag/v1.0.2`. Pages and Release HTML returned HTTP 200 and matched local `index.html` byte for byte (SHA-256 `c93068148bc8731fd60b88f987edc50ba568d6212f5a454569e32cd569583e21`); latest Release API returned v1.0.2 with CORS `*`. Physical phone typing remains unverified.
- Published v1.0.1 at `https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/tag/v1.0.1`. Pages and Release HTML returned HTTP 200 and matched local `index.html` byte for byte (SHA-256 `8392db670d1e7133b68cfe190f63706e64996acd8295713de13e5edaf58d7e6a`); latest Release API returned v1.0.1 with CORS `*`. Physical phone typing remains unverified.
- Published v1.0.0 at `https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/tag/v1.0.0`; Pages is `https://fullmetalsonic.github.io/webcarrot-offline-demo-fms/`.
- At publication, Pages and the Release HTML both returned HTTP 200 and matched local `index.html` byte for byte (SHA-256 `26a5c2a7a313502e3b20e57a98bcc74424b5d27f94c7c5bf2637a9e528492890`). The latest stable Release API returned v1.0.0 with CORS `*`.
- Preserve unknown imported keys and unedited JSON values/types. Parameter count must never cause deletion or migration of backup data.
- Before a requested update, check the live FMS branch HEAD and compare complete menu order, group hierarchy, labels, descriptions, controls, bounds, defaults, choices, vehicle conditions and catalog. Record the source SHA and increment the app version only for an actual demo change.
- Before publishing, check public files for private data and verify schema/source equality, HTML JavaScript syntax, changed-file whitespace, Pages response and Release asset parity. Do not call rendered or phone behavior verified without observing it.

## Limits

- This demo does not contact a Comma device. Online update checks query only public GitHub Release metadata.
- The original demo's local uncommitted driver monitoring work was not copied into this repository. The current FMS schema retains its existing `DisableDM` menu.
- No automatic schedule belongs to this FMS demo.
- Rendered UI and physical phone behavior require separate observation; static parity and publication evidence for each release are recorded above.
