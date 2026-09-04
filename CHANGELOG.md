# Changelog

The version shown under the title (and written into every export as `tool_version` and
into the settings hash) is bumped **only for changes that affect computed numbers** —
landmark detection, alignment, boundary rules, baselines, integration, metrics, QC
thresholds. Documentation, layout and export-format changes do not bump it.

## 1.0 — 2026-09-04
First versioned analysis pipeline: blank subtraction → Hampel spike repair (±0.3 mm, 10σ,
0.003 OD floor) → Savitzky-Golay landmarks (1.5 mm, cubic; prominence ≥ max(0.003 OD, 6σ),
≥ 1.2 mm apart) → 80S-anchored assignment and ladder verdict → alignment at 80S = 32.0 mm
with the 1.5 mm pure-offset test → consensus valleys and auto boundaries (total from the
first-peak onset, monosome g3…g4, polysomes g4…common endpoint − 0.5 mm) → trapezoidal
integration on the unsmoothed data; region-specific baselines (valley-to-valley for
A40/A60); Total AUC, ribosomal AUC, Mono/Poly, Poly/Mono, log2, polysome fraction, free-
subunit fraction, molar 40S:60S (÷ 0.35), heavy fraction; QC thresholds (loading 10 %,
rising end 0.3 mOD/mm); sensitivity grid; per-block contrasts; scale test.
