# High-Performance Search Pipeline for Single-Prime Ramified Number Fields

This repository contains a collection of newly discovered, highly regular 11-degree and 13-degree solvable number fields, characterized by totally real roots and exceptionally clean ramification structures. These computational results are currently being prepared for submission to the **LMFDB (L-functions and Modular Forms Database)**.

## 🏆 Computational Breakthroughs

The search pipeline successfully captured several rare Galois extensions with extreme geometric properties. Most of these fields are **single-prime ramified**:

* **11-Degree Solvable Fields**: Galois groups realized include $C_{11} \rtimes C_5$ and $F_{11}$.
* **13-Degree Solvable Fields**: Galois groups realized include $C_{13} \rtimes C_3$, $C_{13} \rtimes C_4$, and the highly elusive non-abelian semi-direct product **$C_{13} \rtimes C_6$**.

> 📌 **Data Note**: All generated polynomial data can be found in the repository. (A comprehensive list of definitions and raw polynomials is explicitly documented for verification).

## 11th & 13th Degree Polynomials
| Polynomial | Degree | Galois Group | Number Field Discriminant |
| :--- | :--- | :--- | :--- |


## 🔬 Methodology: Class Field Construction Algorithm

The underlying mathematical engine bypasses the immense computational complexity of direct high-degree searches by utilizing a sophisticated **top-down class field tower reduction**:

1. **Base Field Scans**: First, the pipeline searches for lower-degree base fields (e.g., degree 5 or 6) whose class group possesses a structure isomorphic to $C_{11}$ or $C_{13}$.
2. **Unit Root Embedding**: Embed the 11th or 13th roots of unity ($\zeta_{11}$ or $\zeta_{13}$) into the field extension to filter out the target subfields with the precise Galois behavior.
3. **Algebraic Valuation & Power Criteria**: Locate a defining polynomial whose constant term is a perfect 11th or 13th power. The product of roots reducing to the subfield must evaluate to a perfect 11th or 13th power in that local ring, while ensuring the individual roots themselves are not trivial powers.
4. **Radical Extension & Absolute Reduction**: Take the 11th or 13th radical of the polynomial's root, isolate the target 11 or 13-degree subfield, and compute the final optimized defining polynomial using the `polredabs()` algorithm in **PARI/GP**.

## 💻 Requirements & Environment
* **PARI/GP** (for polynomial optimization via `polredabs`)
* **Mathematica** (for structural symmetry analysis)
