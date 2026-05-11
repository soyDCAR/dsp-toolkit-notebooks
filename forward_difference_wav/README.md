# forward_difference_wav

Computes and plots the **forward difference** (discrete first derivative) of the first 30 samples of a `.wav` file.

## Naming note — why not "Delta-Dirac"?

The original project was called *Visualizador de Delta-Dira* (also a typo of "Dirac"). The Dirac delta δ(t) is a
continuous-domain impulse with unit area — not what this code computes. This notebook applies the **forward
difference operator**:

```
Δx[n] = x[n+1] − x[n]
```

which is the standard discrete approximation of the first derivative. The name `forward_difference_wav` reflects
the actual operation.

## Usage

Run the notebook cell. A GUI will open:
1. Click **Cargar Archivo de Audio** and select a `.wav`.
2. The stem plot shows Δx[n] for the first 29 sample intervals.

## Stack

`numpy` · `scipy.io.wavfile` · `matplotlib` · `tkinter`
