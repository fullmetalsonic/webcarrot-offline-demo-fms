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
- Published v1.0.3 at `https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/tag/v1.0.3` from commit `37e5257c62704049e8ea80750a79a70273af768f`. GitHub Pages build for this commit reported `built`; Pages and the Release HTML returned HTTP 200 and matched local `index.html` byte for byte (SHA-256 `f6954154c475d806fb2638c5f2183dcd6441f126b37fa729ee856539230cce76`). JavaScript syntax, exact source schema equality, Git whitespace, and a scoped sensitive-pattern scan passed. Rendered UI and physical phone behavior were not checked.
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

## v1.0.4 numeric controls (2026-10-28)

- Scope: the owner's requested FMS repair and publication. Fix only multiplier order, actual increments, missing narrow-range multiplier controls, and direct integer entry. Preserve FMS settings, existing choices/toggles, Korean IME input, detail navigation, and imported backup values/types.
- The live FMS branch HEAD was `e0f14004a52061895eae47d230327bf03f05065c`. Its `carrot_settings.json` is identical to the embedded `1b1e019` source (193 parameters). `SCHEMA`, `SOURCE_SHA`, and `CAR_CATALOG` remain unchanged; no official-branch DM/settings data was copied.
- The original FMS WebCarrot uses `[1,2,5,10,50,100]` and the selected number as the actual increment, independently of parameter `unit`. Reused the verified official demo's small control fix and adapted its source-pinned regression oracle to FMS. All 98 numeric rows now use this cycle; 59 unit>1 rows no longer multiply the increment twice. Restored the five missing narrow-range controls: CruiseEcoControl, CruiseCoastingPercent, CruiseButtonTest1, CruiseButtonTest3, AutoNaviSpeedCtrlEnd. Numeric number/range entry uses step=1.
- `node --test --test-reporter=tap tests/step-controls.test.cjs`: original product code failed four groups and passed one after correcting a test DOM stub; repaired code passed all five groups. The groups cover all 98 numeric rows, six increments, +/- production handlers and bounds; multiplier visibility/cycle; exact integer input and invalid-value rejection; imported/removed/unknown/nested/type-preserving Blob exports; and existing search-input, choice, and toggle behavior. JavaScript syntax, whitespace, source equality, and the scoped credential/private-data scan passed. No failed product repair attempt remained.
- Public-browser verification passed on code commit `87c6ea75cac87675d17bcdcc6ff2dd0823f4cf8a`: StopDistanceCarrot 600→601→603→608→618→668→768 for increments 1/2/5/10/50/100, then back to x1; direct entry 999; max clamp 1000 and min clamp 400; x1 advances 400→401. At verified viewport 390×844, CruiseEcoControl x5 changes 1→6→1→6 and all its numeric/multiplier buttons fit inside the viewport.
- An actual downloaded JSON from a synthetic eight-key import changed only StopDistanceCarrot and CruiseEcoControl. PaddleMode="4", DisableDM="2", the untouched out-of-range VEgoStopping value, removed key, boolean type, nested unknown data and doubled whitespace remained exact. The first category→search fill completed but Ego reported a disconnected input after the intended DOM replacement; the current page state was inspected and the remaining flow continued without replaying completed actions. This tool verification error was not counted as a failed product repair. Physical-phone testing and full original-screen screenshot parity remain unrun.
- Published `v1.0.4` at `https://github.com/fullmetalsonic/webcarrot-offline-demo-fms/releases/tag/v1.0.4`. Pages build for `87c6ea7` reported `built`. Local HTML, committed HTML, public Pages HTML and the downloaded Release asset are identical: SHA-256 `d09ba30a2056b1de730cb6136f5615ae83aef8caefff7795c347be6530fe9288` (297493 bytes), HTTP 200. Latest Release API returned v1.0.4 with draft=false, prerelease=false and CORS `*`.
