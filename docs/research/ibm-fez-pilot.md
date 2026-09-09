# IBM Fez: a bounded compiler-quality pilot

**September 6, 2026 · Aether AI / Predator research**

[← Project overview](../../README.md) · [Result JSON](ibm-pilot.json)

AQRC’s **joint5** compilation reduced the native two-qubit gate count from **144 to 103** on each of two tested poles. Hardware output moved closer to the corresponding exact ideal distribution on both poles.

This supports a narrow conclusion: a cleaner implementation of the fixed circuits in this acquisition. It does not establish improved optimization or quantum computational advantage.

## Experiment

The pilot used **one six-variable fixture**, its vulnerable and fixed poles, and **one IBM Fez hardware job**. Each pole was compiled through ordinary and joint5 paths, producing four circuits at **1,024 shots each**. The recorded billed QPU time was **3 seconds**.

The objectives, angles, shot counts, and initial physical layout were held fixed. The two poles are related measurements from the same fixture and acquisition, not independent source seeds or independent confirmations.

## Output agreement

Total-variation (TV) distance measures the difference between the measured output distribution and the exact ideal distribution. Lower is better. The site uses the same 0–0.5 display scale for every bar.

| Metric | Vulnerable pole | Fixed pole |
| :--- | ---: | ---: |
| Ordinary TV | 0.3951746961 | 0.4038585827 |
| joint5 TV | 0.3165226488 | 0.3079578516 |
| Absolute improvement | 0.0786520474 | 0.0959007311 |
| Relative TV reduction | 19.9% | 23.7% |
| Native two-qubit gates | 144 → 103 | 144 → 103 |

Relative TV reduction is `(ordinary TV − joint5 TV) / ordinary TV`. Gate reduction is `(144 − 103) / 144 = 28.47%`, displayed as **28.5%**.

## Uncertainty

The sampling-only 95% intervals for ordinary-minus-joint5 TV improvement are:

| Pole | Sampling-only 95% interval |
| :--- | :--- |
| Vulnerable | [0.036615, 0.117400] |
| Fixed | [0.052002, 0.135952] |

These are plug-in percentile intervals from **2,000 independent multinomial bootstrap replicates per arm**, seed **20260906**. They cover sampling uncertainty, not calibration drift or an independently repeated experiment. Independent confirmation has not been performed.

## Optimization is a different question

Expected energy increased under joint5, which is worse for this minimization objective:

| Metric | Ordinary | joint5 |
| :--- | ---: | ---: |
| Vulnerable expected energy | −2.345352 | −2.013768 |
| Fixed expected energy | −2.366837 | −1.954590 |
| Vulnerable exact-optimum hits / 1,024 | 0 | 1 |
| Fixed exact-optimum hits / 1,024 | 2 | 2 |

Closer agreement with a fixed ideal distribution does not itself establish better objective values. These results do not establish source-detection gains, improved deep-chain feedback, quantum computational advantage, or supremacy.

## Provenance

This is an **author-reported public extract** of the retained September 6 pilot report and metrics. It includes a curated numerical summary, not raw acquisition artifacts, executable circuits, or the proprietary implementation. Fingerprints identify the source artifacts; they do not independently verify the measurements.

| Retained artifact | SHA-256 |
| :--- | :--- |
| Metrics | `96fc51fc142d3e315084e4d1d215d06abe41b5c57737bc7e14c6305bae1dd304` |
| Pilot report | `b1e83633a85b533fba1fb4f4fde97151ee1f68442818b7e5b22cfb5b9e6414d4` |
| Compiled plan | `a986dcc6c83b2c68294044b93d64434cb221bf7cef49ba7f32557e8f5d1950e1` |

Full-precision public values are available in [ibm-pilot.json](ibm-pilot.json). For research discussion, [contact Aether AI](https://aethersystems.net/).

IBM is identified as the hardware provider. No IBM affiliation or endorsement is implied.
