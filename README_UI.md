# Stockland Ethiopia — UI Last Pass

This branch contains an isolated, responsive UI preview based on the current Stockland ERP GitHub source conventions. It focuses on the reported invisible global search, host-theme CSS collisions, and the missing Bootstrap-to-SaaS theme bridge.

## Files
- ui/index.html — self-contained responsive command-center preview with scoped toolbar/search CSS.
- ui/UI_AUDIT.md — source findings, integration notes and acceptance boundaries.

## What changed
- Increased specificity and isolation for the topbar/search wrapper/input/results panel under #stockland-app.
- Search is placed in its own row below 992px and gets a deliberate desktop grid column.
- Stockland navy/blue/teal/violet/amber/emerald colors and explicit Bootstrap light-theme semantic tokens.
- Keyboard shortcut Ctrl/Cmd+K, arrow-key navigation, Enter/Escape behavior, and hidden result panel state.
- Blank operational KPIs and an explicit API disconnected notice; no fake sales or stock values.

## Critical boundary
The source repo aistockland-web/Erp began with only LICENSE and a minimal README. This branch is a standalone UI preview, not a replacement WordPress ERP plugin. It has no database, authentication, sales, stock, finance, procurement or payroll backend. Its search finds workspace shortcuts only.

The existing ERP source is in stocklandethiopia/stockland-erp-project and its main branch was identified as release 16.1.78. The global search UI there uses #slGlobalSearch and #slGlobalSearchResults and calls the permission-scoped /app/global-search?q=... endpoint. When integrating the style hardening into the production plugin, preserve that route, authorization, current IDs and keyboard/ARIA behavior; do not substitute this preview's shortcut search.

## Before production integration
1. Port the scoped CSS hardening into the six canonical CSS modules in the WordPress plugin.
2. Rebuild assets/app.css and assets/app.min.css with the repository's tools/qa/rebuild-css.py.
3. Run the existing static QA scripts, PHP/JS lint and Semgrep.
4. Browser-test 320, 390, 768, 1024, 1440 and 1920 widths with host theme styles loaded after the ERP CSS.
5. Verify authenticated search results, server-side branch/capability scoping, live data, backup/restore and rollback on staging/target host.

No production backend or operational data was changed by this branch.
