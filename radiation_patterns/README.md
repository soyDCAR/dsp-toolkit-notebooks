# radiation_patterns

Polar radiation pattern simulator for acoustic multipole sources.

## Models

All models use the acoustic multipole formulation. The wave number is `k = 2πf / c`.

| Source | Formula | Pattern |
|--------|---------|---------|
| Monopole | `(A/R) · e^{−jkR}` | Omnidirectional sphere |
| Dipole | `(A/R) · 2j·sin(k·d/2·sinθ)` | Figure-eight |
| Tripole + | `(A/R) · [1 − 2cos(kd·sinθ)]` | Asymmetric cardioid |
| Tripole − | `(A/R) · [−1 + 2cos(kd·sinθ)]` | Inverted asymmetric |
| Quadrupole | Complex sum with weights 7/8, 1/4, 3/4 | Four-lobe |

## Configuration

Physical parameters are centralized in the `CONFIG` dict at the top of the notebook (frequency, sound speed, source separation, amplitude, observer distance). Fields are pre-populated in the GUI from these defaults.

## Usage

Run the notebook cell. Set parameters, choose source type, click **Graficar**.

## Stack

`numpy` · `matplotlib` · `tkinter`
