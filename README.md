# Paramodular Conjecture for the Goldbach–Frey Jacobian

**Author:** Ruqing Chen, GUT Geoservice Inc., Montréal, QC, Canada

## Paper

> R. Chen, *Paramodular Conjecture for the Goldbach–Frey Jacobian: From GSp(4) to Bianchi Modularity via Weil Restriction*, Zenodo, 2026.

The Brumer–Kramer paramodular conjecture predicts that every abelian surface over Q with trivial endomorphism ring corresponds to a weight-2 Siegel paramodular newform. This paper applies the conjecture to the Goldbach–Frey Jacobian Jac(C\_{N,p}) and proves that the Weil restriction structure Jac ~ Res\_{K/Q}(E\_p) reduces the GSp(4) problem to the modularity of an elliptic curve E\_p over K = Q(√−1), where existing modularity lifting theorems (the ten-author theorem) can be applied at ℓ = 3.

This is the eighth paper in the conductor rigidity series:

| # | Paper | Zenodo |
|---|-------|--------|
| 1 | Conductor Incompressibility for Frey Curves | [18682375](https://zenodo.org/records/18682375) |
| 2 | Density Thresholds for Equidistribution | [18682721](https://zenodo.org/records/18682721) |
| 3 | Weil Restriction Rigidity via Genus 2 Jacobians | [18683194](https://zenodo.org/records/18683194) |
| 4 | On Landau's Fourth Problem | [18683712](https://zenodo.org/records/18683712) |
| 5 | The 2-2 Coincidence | [18684151](https://zenodo.org/records/18684151) |
| 6 | Genesis of Prime Constellations (GSp(8)) | [18684352](https://zenodo.org/records/18684352) |
| 7 | The Goldbach Mirror (Static Conduit) | *forthcoming* |
| 8 | **Paramodular Conjecture** (this paper) | *forthcoming* |

## Repository Contents

```
├── README.md
├── Paramodular_Goldbach_Frey_v2.tex      # LaTeX source
├── Paramodular_Goldbach_Frey_v2.pdf      # Compiled paper
├── scripts/
│   ├── verify_conductor.py               # Theorem 2.1: explicit conductor
│   ├── verify_toric_rank.py              # Dual graph and Kani-Rosen analysis
│   └── verify_residual.py                # Proposition 4.1: residual representations
└── data/
    └── conductor_table.csv               # Conductor factorizations for N ≤ 100
```

## Scripts

### verify_conductor.py — Theorem 2.1 Verification

Tests all four cases of the conductor exponent computation:

- **(i) Boundary primes:** additive reduction at p and 2N−p, ord\_r(Δ) ≥ 6
- **(ii) Static conduit:** f\_r = 2 at primes dividing N, verified uniform across the family
- **(iii) Dynamic conduit:** f\_r = 2 at primes dividing N−p
- **Cross-check:** formula Δ = 2¹² p⁶(2N−p)⁶(N−p)⁴N⁴ matches direct root computation

```bash
cd scripts && python3 verify_conductor.py
```

### verify_toric_rank.py — Dual Graph and Splitting Analysis

Verifies:
- Dual graph has b₁ = 2 for two nodes on an irreducible curve
- Local Euler factor at semistable primes is (1−r⁻ˢ)⁻²
- Kani-Rosen eigenvalues (+i, −i) with multiplicity 1 each
- **Refutation** of the erroneous claim that Jac splits over Q via x → x + pq/x (the substitution Y₁ = y/x^{3/2} involves √x, which is not a rational function on the curve)

```bash
cd scripts && python3 verify_toric_rank.py
```

### verify_residual.py — Proposition 4.1 Verification

Analyzes the residual Galois representations:
- **ℓ = 2:** all 2-torsion is Q-rational (universal obstruction)
- **ℓ = 3:** statistics on when 3 divides the various discriminant factors; generic absolute irreducibility argument
- Generates `data/conductor_table.csv` with conductor factorizations

```bash
cd scripts && python3 verify_residual.py
```

## Data

### conductor_table.csv

Precomputed conductor data for 554 Goldbach pairs (p, 2N−p) with N ≤ 100. Columns:

| Column | Description |
|--------|-------------|
| `2N` | Even number |
| `p`, `q` | Prime pair with p + q = 2N |
| `N`, `N-p` | Static and dynamic conduit bases |
| `ord_2(Delta)` | Always 12 (when p, q are odd primes) |
| `static_conduit_primes` | Odd prime factors of N not dividing p or q |
| `dynamic_conduit_primes` | Odd prime factors of N−p not dividing N, p, or q |
| `boundary_type` | "small" if p=3 or q=3, else "generic" |

## Key Results

| Result | Status | Reference |
|--------|--------|-----------|
| Explicit conductor N\_Jac | **Unconditional** | Theorem 2.1 |
| Paramodular ⟺ Bianchi modularity | **Unconditional** | Theorem 3.1 |
| ℓ=2 universally blocked | **Unconditional** | Proposition 4.1(i) |
| ℓ=3 generically irreducible | **Expected** | Proposition 4.1(ii) |
| Modularity of E\_p/K | **Conditional** | Theorem 4.3 |
| Almost-all paramodular | **Conditional** | Corollary 5.2 |

## Requirements

- Python 3.6+
- No external dependencies

## License

MIT License
