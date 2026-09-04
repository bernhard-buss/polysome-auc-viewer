# Polysome AUC Viewer

**Open the tool:** https://bernhard-buss.github.io/polysome-auc-viewer/

A single-file, dependency-free browser tool for polysome profiles exported from a
BioComp Gradient Station / Triax flow cell (`.csv`) or plain two-column position/OD
files. Everything runs locally in your browser — **no data leaves the page**.

Features: drag-to-set monosome/polysome regions, three baseline modes (+ anchored
piecewise-linear), per-run alignment at the 80S peak, spike (bubble) detection and
removal, outcome-independent QC flags, boundary-sensitivity check, Mono/Poly,
Poly/Mono and log2 ratios, optional heavy-polysome fraction, CSV and Excel export
(native charts).

## Development

This repository is the source of truth. The whole tool is `index.html` (HTML + CSS +
JS, no build step); GitHub Pages serves `main` directly, so every push to `main`
updates the public URL within about a minute. To work on it locally, open
`index.html` in a browser (or serve the folder with any static server).

## License

MIT — see [LICENSE](LICENSE). Copyright (c) 2026 ETH Zurich.
