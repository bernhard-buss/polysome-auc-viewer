# Polysome AUC Viewer — notes for Claude Code

- The entire tool is `index.html` (HTML + CSS + JS, no build step, no dependencies,
  no CDN). GitHub Pages serves `main` directly at
  https://bernhard-buss.github.io/polysome-auc-viewer/ — every push to `main` is live
  within about a minute, so keep `main` working.
- Test hook: `window.__pav` exposes `addFileText(text, name)`, `setBounds(m1, m2, p3, h)`,
  `results()`, `traces()`, `sensitivity()`, `buildXlsx()` for driving the page from
  the Browser pane. The Excel writer is hand-rolled OOXML; validate exported
  workbooks with openpyxl after changing it.
- Never add data files here. Real instrument traces used for testing live outside
  this repository (a private sibling project); serve them locally instead.
