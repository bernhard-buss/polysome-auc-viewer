# Polysome AUC Viewer

**Open the tool:** https://bernhard-buss.github.io/polysome-auc-viewer/

A single-file, dependency-free browser tool for polysome profiles exported from a
BioComp Gradient Station / Triax flow cell (`.csv`) or plain two-column position/OD
files. Everything runs locally in your browser — **no data leaves the page**.

Features: automatic landmarks (free-RNA peak, 40S/60S/80S, polysome peaks, valleys) on a
Savitzky-Golay-smoothed, despiked trace; alignment at the 80S with a pure-offset check;
rule-based boundaries (valley-to-valley) with a common endpoint; blank-gradient
subtraction; region-specific baselines; Total AUC (loading), Mono/Poly, Poly/Mono, log2,
polysome fraction, A40/A60, free-subunit fraction, molar 40S:60S, heavy fraction; the polysome
size distribution — the polysome window cut into 2-, 3-, 4-mer regions and a tail at the
ladder valleys (midpoint fallback for shallow valleys), with shares, heavy/light, ribosomes per
polysomal mRNA and a boundary uncertainty per region; per-region cross-sample ratios (per-block
log2 with a cut-shift range, four normalisations);
outcome-independent QC flags (spikes, negative OD/area, loading, gradient scale, rising
end, non-linear first peak, scan-order confounding); boundary × baseline sensitivity grid;
per-block contrasts with a paired t; pairwise scale test; settings lock with hash; CSV,
tidy CSV and Excel export (native charts).

## Versioning

The version under the title is bumped only for changes that affect computed numbers and is
written into every export (`tool_version`) and into the settings hash; see [CHANGELOG.md](CHANGELOG.md).

## Development

This repository is the source of truth. The whole tool is `index.html` (HTML + CSS +
JS, no build step); GitHub Pages serves `main` directly, so every push to `main`
updates the public URL within about a minute. To work on it locally, open
`index.html` in a browser (or serve the folder with any static server).

## License

MIT — see [LICENSE](LICENSE). Copyright (c) 2026 ETH Zurich.
