# Polysome AUC Viewer — notes for Claude Code

- The entire tool is `index.html` (HTML + CSS + JS, no build step, no dependencies,
  no CDN). GitHub Pages serves `main` directly at
  https://bernhard-buss.github.io/polysome-auc-viewer/ — every push to `main` is live
  within about a minute, so keep `main` working.
- Test hook: `window.__pav` exposes `addFileText(text, name)`, `setBounds(m1, m2, p3, h, t0)`,
  `results()`, `traces()`, `landmarks()`, `autoBounds()`, `setBlank(i)`, `sensitivity()`,
  `contrastTable()`, `scalePairs()`, `tidyCsv()`, `settingsHash()`, `buildXlsx()` for driving
  the page from the Browser pane.
- Pipeline order matters: blank subtraction -> Hampel despike -> Savitzky-Golay (landmarks
  only) -> landmarks -> alignment (80S at 32.0 mm) -> consensus -> auto boundaries;
  integration always on the unsmoothed series. The Excel writer is hand-rolled OOXML; validate exported
  workbooks with openpyxl after changing it.
- Never add data files here. Real instrument traces used for testing live outside
  this repository (a private sibling project); serve them locally instead.
