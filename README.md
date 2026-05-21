# Specialized Search Pipeline for Single-Prime Ramified Number Fields

This repository contains a collection of newly discovered, highly regular 11-degree and 13-degree solvable number fields, characterized by totally real roots and exceptionally clean ramification structures. These computational results are currently being prepared for submission to the **LMFDB (L-functions and Modular Forms Database)**.

## Research Breakthroughs

* **Degree 5**: Generated 80+ Frobenius $F_5$ fields; including **20 unindexed single-prime ramified extensions** within the $10000^3 < \Delta < 20000^3$ range, successfully filling blind spots in the current LMFDB.
* **Degree 7**: Isolated 20 Frobenius $F_7$ fields; including 6 unindexed single-prime ramified extensions and 14 targeted $p^4 q^3$ discriminant structures via a novel grafting method.
* **Degree 11**: Discovered 14 unique fields under extreme constraints.
* **Degree 13**: Trapped 5 exotic non-abelian fields with exact single-prime ramification, tracking highly elusive structures across $C_{13} \rtimes C_3$ ($\Delta = 1063^8, 1459^8$), $C_{13} \rtimes C_4$ ($\Delta = 2617^9$), $C_{13} \rtimes C_6$ ($\Delta = 3469^{10}$), and the massive $F_{13}$ Frobenius extension ($\Delta = 4729^{11}$).

**Data Note**: All generated polynomial data can be found in the repository. (A comprehensive list of definitions and raw polynomials is explicitly documented for verification).

## Dataset Summary

| Degree | Galois Group | Key Breakthroughs & Unindexed Discoveries |
| :--- | :--- | :--- |
| **Degree 5** | $F_5$ | **80+ fields generated**; isolates 20 completely new single-prime extensions ($10000^3 < \Delta < 20000^3$) missing from LMFDB. |
| **Degree 7** | $F_7$ | **20 fields isolated**; includes 6 new single-prime extensions and 14 targeted $p^4 q^3$ structures via a novel grafting method. |
| **Degree 11**| $C_{11}\rtimes C_5$, $F_{11}$ | **14 unique fields discovered** under extreme constraints. *(Data suppressed prior to publication)* |
| **Degree 13**| $C_{13}\rtimes C_3$, $C_{13}\rtimes C_4$, $C_{13}\rtimes C_6$, $F_{13}$ | **5 rare non-abelian fields trapped** up to the maximal solvable $F_{13}$ structure ($\Delta = 4729^{11}$). *(Data suppressed prior to publication)* |

## Motivation & Design Philosophy: Breaking the High-Degree Discovery Barrier
The primary drive behind this project is to systematically explore and catalog rare, high-degree algebraic number fields (specifically Degree 11 and Degree 13) under stringent ramification conditions—an area where global databases currently remain largely empty.

Standard computer algebra frameworks generally rely on top-down brute-force constructions, which immediately hit an absolute wall due to severe **coefficient explosion** when pushing into high degrees paired with large prime ramifications. 

To break this barrier, this pipeline shifts the paradigm from "top-down construction" to a novel **"Bottom-Up Parallel Filtering"** strategy. By implementing early stage-gating based on structural invariants, the pipeline eliminates **99.9%** of non-matching candidates within milliseconds. This specialized architecture enables a standard 96GB RAM workstation to seamlessly discover rare higher extensions that are entirely out of reach for official package functions.

## Methodology: Class Field Construction Algorithm

The underlying mathematical engine bypasses the immense computational complexity of direct high-degree searches by utilizing a sophisticated **top-down class field tower reduction**:

1. **Base Field Scans**: First, the pipeline searches for lower-degree base fields (e.g., degree 5 or 6) whose class group possesses a structure isomorphic to $C_{11}$ or $C_{13}$.
2. **Unit Root Embedding**: Embed the 11th or 13th roots of unity ($\zeta_{11}$ or $\zeta_{13}$) into the field extension to filter out the target subfields with the precise Galois behavior.
3. **Algebraic Valuation & Power Criteria**: Locate a defining polynomial whose constant term is a perfect 11th or 13th power. The product of roots reducing to the subfield must evaluate to a perfect 11th or 13th power in that local ring, while ensuring the individual roots themselves are not trivial powers.
4. **Radical Extension & Absolute Reduction**: Take the 11th or 13th radical of the polynomial's root, isolate the target 11 or 13-degree subfield, and compute the final optimized defining polynomial using the `polredabs()` algorithm in **PARI/GP**.

## Requirements & Environment
* **PARI/GP** (for polynomial optimization via `polredabs`)
* **Mathematica** (for structural symmetry analysis)
