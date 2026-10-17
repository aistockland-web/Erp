# Stockland Ethiopia ERP — UI Preview

This repository currently contains a **standalone, responsive UI last-pass preview**. The source preview is [ui/index.html](ui/index.html); its source-level audit and production integration boundary are documented in [ui/UI_AUDIT.md](ui/UI_AUDIT.md).

## Focus of this UI pass
- Keep the global search visible under generic header/input theme resets.
- Use an isolated, responsive header grid with a dedicated search row on tablet/mobile.
- Harmonize Stockland navy, blue, teal, violet, amber and green styling and Bootstrap light-theme tokens.
- Preserve keyboard navigation, the visible/hidden results panel states and focus indicators.
- Keep live business metrics blank until authenticated ERP data is connected.

## Important — not a production ERP plugin
The original production WordPress ERP source lives in [stocklandethiopia/stockland-erp-project](https://github.com/stocklandethiopia/stockland-erp-project). That repo's main branch was verified as source release 16.1.78. This repo was initially empty apart from its license and this minimal README.

The UI here is **preview-only**. It has no database, authenticated API, role enforcement, inventory posting, sales, ledger, AP/AR, procurement or payroll. Search matches workspace shortcuts only. Do not install this as a WordPress plugin or treat the preview as a live application.

Before applying the CSS strategy to production, port it into the existing ERP's six canonical CSS modules, rebuild the compiled stylesheet, run the existing QA and security checks, and validate against the authenticated WordPress site and a rollback-capable backup.
