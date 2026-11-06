# Stockland ERP UI Last-Pass — Source Audit

## Repository discovery
Target repository: aistockland-web/Erp. Initial main commit: 90627f6d14c5e4186166d9910f8a6e8af74c12ca. Its recursive tree initially contained only LICENSE and a 5-byte README.md; it did not contain an ERP plugin or business application files. The UI has therefore been added under ui/ as a separate preview, not grafted into a nonexistent plugin.

Comparison repository: stocklandethiopia/stockland-erp-project, main commit 6bb6288633929f020d1869e54e607ee9f3261886, plugin/manifest release 16.1.78.

## Confirmed upstream source facts
- Global search markup, event handlers and the permission-scoped /app/global-search?q=... API call exist.
- Bootstrap 5.3.8 is bundled and the canonical CSS build is not missing its search styles: app.css matches the concatenation of the six source modules, and app.min.css matches the repository minification algorithm.
- The CSS search selectors are not consistently isolated from generic host-theme CSS, which is a plausible override path but not a confirmed live computed-style diagnosis.
- The frontend source checked has no explicit data-bs-theme integration; Bootstrap being present does not automatically theme custom .sl-* components.
- The current release manifest marks exact source/package CI and target-host acceptance as pending.

## Candidate UI repair
- Scope toolbar/search selectors under #stockland-app; force visibility and sizing against broad theme resets.
- Keep desktop search in its own grid column; place it on a dedicated row at tablet/phone breakpoints.
- Map Bootstrap semantic body/text/background/primary/border/link/focus/font tokens to the Stockland palette.
- Add keyboard-accessible workspace lookup and a responsive sidebar/nav shell for visual review.
- Do not fabricate live operating metrics; all values stay blank until authenticated APIs are connected.

## Validation status
The HTML is self-contained with no CDN runtime dependencies. It requires a browser smoke at viewport widths 320, 390, 768, 1024, 1440 and 1920, including host-style override simulation. A browser smoke run in the previous local environment timed out, so no visual/browser pass is claimed here. This branch is not a production ERP plugin and must not be deployed as one.

## Production handoff
Merge the CSS strategy into the existing six source modules and rebuild the actual production assets. Keep the production app.js and its authenticated global-search route untouched. Run the existing test suite and create evidence from the actual authenticated WordPress site before deployment.
