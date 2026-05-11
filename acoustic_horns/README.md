# acoustic_horns

2D cross-sectional profile and 3D surface-of-revolution plotter for four acoustic horn expansion laws.

## Horn types

| Type | Area law S(x) | Notes |
|------|--------------|-------|
| Cónica | `ST·(x/x₀)²` | Quadratic expansion, no cut-off frequency |
| Exponencial | `ST·e^(mx)` | Lowest cut-off, widest pass-band |
| Catenoidal | `ST·cosh²(mx/2)` | Special case of hyperbolic with M = 0 |
| Hiperbólica | `ST·[cosh(mx/2) + M·sinh(mx/2)]²` | Generalized (0 < M < 1) |

**Parameters:** `ST` = throat area [m²], `m` = flare rate [1/m], `M` = hyperbolic shape factor, `x₀` = reference length for conic horn [m].

## Usage

Run the notebook cell. Select horn type, fill in parameters, click **Graficar**. Two panels appear:
- Left: S(x) profile (area vs. distance).
- Right: 3D surface of revolution around the x-axis.

## Stack

`numpy` · `matplotlib` (including `mpl_toolkits.mplot3d`) · `tkinter`
