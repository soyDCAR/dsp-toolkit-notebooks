# DSP Toolkit Notebooks

A collection of interactive Python/Jupyter tools for digital signal processing and acoustics.
Each module is a self-contained notebook with a `tkinter` + `matplotlib` GUI — no configuration needed beyond `pip install`.

## Modules

| Module | Description | Stack |
|--------|-------------|-------|
| [`third_octave_eq`](third_octave_eq/) | 32-band 1/3-octave graphic equalizer with real-time FFT and waveform visualization | numpy, scipy, matplotlib |
| [`wav_speed_shifter`](wav_speed_shifter/) | WAV speed change via resampling (×2 / ×0.5) — note: affects pitch | numpy, scipy |
| [`forward_difference_wav`](forward_difference_wav/) | Discrete first derivative (forward difference Δx[n] = x[n+1]−x[n]) of WAV signals | numpy, scipy, matplotlib |
| [`discrete_convolution`](discrete_convolution/) | Discrete convolution calculator: direct method vs. sum method, sequences of any length | numpy |
| [`radiation_patterns`](radiation_patterns/) | Acoustic multipole radiation pattern simulator — monopole, dipole, tripole, quadrupole | numpy, matplotlib |
| [`acoustic_horns`](acoustic_horns/) | 2D profile + 3D revolution plotter for conic, exponential, catenoidal and hyperbolic horns | numpy, matplotlib |

## Installation

```bash
pip install numpy scipy matplotlib
```

> `tkinter` is bundled with Python on Windows and macOS.
> On Linux: `sudo apt install python3-tk`

## Usage

Open any module notebook in Jupyter Lab or Notebook and run the single code cell. A GUI window will launch.

```bash
jupyter lab discrete_convolution/discrete_convolution.ipynb
```

## Notable fixes in this consolidation

- **`discrete_convolution`** — removed a hardcoded `min(11, len(X))` magic number that silently capped convolution to 11 samples, producing wrong results for longer sequences. See [`discrete_convolution/README.md`](discrete_convolution/README.md).
- **`forward_difference_wav`** — renamed from *Visualizador de Delta-Dira*. The original name contained both a typo ("Dira" → "Dirac") and a conceptual error: the code computes a forward difference, not a Dirac delta. See [`forward_difference_wav/README.md`](forward_difference_wav/README.md).
- **`radiation_patterns`** — physical constants (frequency, sound speed, etc.) centralized in a `CONFIG` dict; GUI fields pre-populated from defaults.
- **`acoustic_horns`** — embedded cell outputs stripped, reducing file size from ~230 KB to ~7 KB.

## Future work

- [ ] **Phase Vocoder** in `wav_speed_shifter`: time-stretching without pitch change (STFT-based).
- [ ] **Export equalized audio** in `third_octave_eq`: save filtered signal as `.wav`.
- [ ] **Full-signal analysis** in `forward_difference_wav`: second derivative, spectrogram.
- [ ] **Load sequences from file** in `discrete_convolution`: CSV or WAV input for X[n] and h[n].
- [ ] **dB SPL scale** in `radiation_patterns`: normalized magnitude in dB with contour lines.
- [ ] **Cut-off frequency display** in `acoustic_horns`: compute and annotate `f_c = mc/(4π)`.

## Author

Dilan Acosta

## License

MIT — see [LICENSE](LICENSE).
