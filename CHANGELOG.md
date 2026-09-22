# Changelog

The version shown under the title (and written into every export as `tool_version` and
into the settings hash) is bumped **only for changes that affect computed numbers** —
landmark detection, alignment, boundary rules, baselines, integration, metrics, QC
thresholds. Documentation, layout and export-format changes do not bump it.

## 1.3 — 2026-09-22
Polysome size distribution. The polysome window is cut into one partition of n-mer
regions at the consensus ladder valleys — a valley is used as a cut when its median
relative depth (drop below the apex-to-apex line, over the lower apex's height above the
flat minimum) is ≥ 10 %, otherwise the cut falls to the midpoint between the two apexes;
the tail "≥ n" starts at the last usable cut, which is now also the auto heavy boundary
(it was fixed at the 3|4 valley). Every region uses the polysome baseline, so the regions
add up to Apoly exactly. New per sample: A2 … A_tail, shares of Apoly, ratios to the
monosome, heavy / light = (≥4-mer) / (2-mer + 3-mer) (also in the main table), ribosomes
per polysomal mRNA = ΣA_n / Σ(A_n / n) with the tail counted at its lower-bound n (a lower
bound), and a boundary uncertainty per region (OD above baseline at each edge × 0.5 mm, as a
fraction of the area). Per-region contrasts: per-block log2(A/B) of each region's
normalised area (share of mono + poly by default; per ribosomal AUC, per loaded A260 or raw
selectable — the normalisation is part of the settings hash) with the range over every cut
moved ± 0.5 mm. Exports carry the new columns, a Regions sheet with a stacked bar chart,
and the region contrasts. Poly/Mono, A40/A60 and everything outside the polysome partition
are unchanged; A2/A3 keep their values wherever the 2|3 and 3|4 valleys are usable cuts.

## 1.2 — 2026-09-04
Optional alignment mode "shift + scale": per-sample least-squares x = a + b·x_ref on the
40S/60S/80S/disome/trisome landmarks against their shift-only consensus (linear only);
|b − 1| > 5 % flagged as a different gradient; areas integrated in native mm so they are
not scaled by b; b reported per sample and in all exports. Default (shift only) results
are identical to 1.1.

## 1.1 — 2026-09-04
Polysome ladder landmarks: 2-, 3-, 4- (and 5-)mer assigned by a windowed search — relaxed
candidates (peaks ≥ max(0.0008 OD, 1.5σ) plus curvature shoulders), disome 1.6–2.7
subunit steps after the 80S, each next n-mer at 0.4–0.9 of the previous spacing; valleys
between n-mers as detrended minima. New outputs: A2 (disome), A3 (trisome), n-mer
positions; the heavy (≥4-mer) boundary is auto-set at the 3|4 valley when 2-/3-/4-mer are
assigned (heavy fraction therefore reported by default where it was off before). The
ladder verdict rule replaces the former 1.1–2.0× disome test. Everything else unchanged.

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
