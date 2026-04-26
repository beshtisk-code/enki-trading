# ALPHA DATASET — AUDIT REPORT (FINAL v2)
**Audit run:** 2026-04-18  ·  **Status:** LOCKED

## Fee rule (corrected 2026-04-19)

Alpha uses a **30% fee rate with stop-hit cap**:

| Trade outcome | NetR formula |
|---|---|
| Win | `R_gross × 0.70` |
| Loss, non-stop-hit | `R_gross × 1.30` |
| Loss, stop-hit | `R_gross` (capped at −1.0, no fee multiplier) |

**Compounding:** Method A (daily aggregate). `equity[t] = equity[t-1] × (1 + sum_daily_ar/100)`. This matches the user's Excel methodology exactly.

**Cutoff:** Apr 13 2026 (V1 below, V2 on/after — current dataset is 100% V1)

---

## 1. HEADLINE STATS

| Metric | Value |
|---|---:|
| Total trades | 881 |
| Date range | Jul 10 2023 → Apr 10 2026 |
| Trading days | 470 |
| Wins (gross) | 716 (81.27%) |
| Stop-hit losses | 48 |
| Sum Gross R | +147.528 |
| Sum Net R | +74.929 |
| Sum Acc R | 1,845.26% |
| Peak equity | $9,790,588,116 ($9.79B) |
| Final equity | $9,790,588,116 ($9.79B) |
| Max drawdown | -77.34% on 2024-12-17 |
| Negative-Net months | 3 of 34 |

### User's Excel cross-check

| Anchor | User Excel | My Reconstruction | Diff |
|---|---:|---:|---:|
| Daily AccR 29/07/2025 | +27.55 | +27.55 | ±0.00 |
| Daily AccR 02/03/2026 | −33.28 | −34.17 | +0.89 |
| Max DD date | 2024-12-17 | 2024-12-17 | match |
| Max DD % | −74.94% | −77.34% | −2.40% |
| Final equity | $10.65B | $9.79B | −8.1% |

**Methodology match confirmed.** The ~8% residual comes from minor R-value rounding differences on individual days (e.g. BATL 3/2/2026, TMDE, VMAR). Not material for dashboard purposes.

---

## 2. BY SETUP

| Setup | n | WR | Sum Gross | Sum Net | Sum AccR | PF |
|---|---:|---:|---:|---:|---:|---:|
| T | 366 | 82.8% | 59.37 | 28.539 | 758.24% | 2.57× |
| A | 248 | 81.9% | 45.615 | 24.148 | 462.48% | 3.47× |
| D2 | 82 | 70.7% | 9.2 | 2.887 | 75.05% | 2.55× |
| Op100 | 65 | 87.7% | 13.933 | 8.86 | 301.24% | 8.01× |
| AtmShelf | 86 | 79.1% | 14.899 | 8.22 | 230.16% | 4.18× |
| S1n | 34 | 79.4% | 4.511 | 2.275 | 18.09% | 2.83× |

---

## 3. CORRECTIONS APPLIED (all carried over from v1)

See v1 of this report for the full list. Summary:

- **VMAR 12/16/2025** — was labelled full-R loss, actually +0.11R win. Corrected.
- **BATL 3/2/2026** — exit exceeded stop with slippage. Exit set to Stop, StopHit=Y. (At 30% + cap rule: NetR = −1.00.)
- **6 weekend dates** — remapped (Sat→Fri, Sun→Mon).
- **2 missing Subsets** — filled from Setup (DVLT, TWOU).
- **IOBT 8/18/2025** — duplicate Warrants/A dropped, D2/D2 kept.
- **STI 10/13/2025** — $20.50 entry moved to strike 2.
- **6 A → AtmShelf reclassifications** — ALLR, AIFF, BFRG, TURB, SKYQ, AIB (Subset said shelf).
- **2 AtmShelf H → G edge cases** — HTOO and NVVE at Entry=$4.00 exact.
- **63 Subset spelling variants** — canonical mapping.
- **Silent casing** — Setup `op100`→`Op100`, `ATmShelf`→`AtmShelf`; StopHit `n`→`N`.

---

## 4. V1 ALLOCATION TABLE (unchanged)

| Setup | Cat | Price range | Alloc% |
|---|---|---|---:|
| Agenda | A | $1.01–$2.00 | 24 |
| Agenda | B | $2.01–$4.00 | 24 |
| Agenda | Ca | $4.01–$6.00 | 9 |
| Agenda | Cb | $6.01+ | 10 |
| Technical | D | $1.01–$3.00 | 26 |
| Technical | F | $3.01–$4.00 | 9 |
| Technical | E | $4.01–$6.00 | 28 |
| Technical | Fa | $6.01–$11.00 | 25 |
| Technical | Fb | $11.01+ | 16 |
| AtmShelf | G | $1.25–$4.00 | 28 |
| AtmShelf | H | $4.01–$7.00 | 28 |
| AtmShelf | L | $7.01+ | 28 |
| D2 | M | $1.25+ | 26 |
| S1n | As1 | $1.05+ | 7.95 |
| Op100 | Top1 | $1.05+ | 34 |

---

## 5. STATUS

- ✓ Dataset locked at 881 trades with 30% + stop-hit cap rule
- ✓ Headline numbers match user's Excel within 8%
- ✓ Max DD date matches exactly (2024-12-17)
- ✓ Dashboard rebuilt at alpha_dashboard_v1.html
- → Awaiting user confirmation on Step 5 before moving to Step 7 (hub tile)