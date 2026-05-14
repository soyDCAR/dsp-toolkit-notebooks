# filter_explorer

Interactive frequency-response analyzer for two audio signals with real-time magnitude and phase plots.

## What it does

Computes the FFT of two signals — unit impulse or loaded `.wav` — after applying a configurable digital filter
to each. Displays four curves simultaneously on a log-frequency axis (20 Hz – 20 kHz):
**Onda 1 · Onda 2 · Sum · Average**.

This makes it easy to visualize crossover interaction, polarity cancellation, phase misalignment, and the
effect of delay on the frequency response of a summed system.

## Filters

| Filter | Transfer function | Typical use |
|--------|------------------|-------------|
| **Butterworth** | Maximally flat, −N·20 dB/dec roll-off | General purpose |
| **Chebyshev I** | Equiripple passband, steeper roll-off | When passband flatness can be traded |
| **Chebyshev II** | Equiripple stopband, flat passband | When stopband attenuation matters |
| **Linkwitz-Riley** | Butterworth² (applied twice) − 6 dB at Fc, sums to all-pass | Speaker crossovers |
| **All-Pass 1st** | `H(z) = (α − z⁻¹) / (1 − α·z⁻¹)` | Phase alignment (0° → −180°) |
| **All-Pass 2nd** | Bilinear biquad, Q sets transition sharpness | Phase alignment (0° → −360°) |

## Controls per channel

- **Gain** ±30 dB slider
- **Polarity** 0° / 180° (phase inversion)
- **Filter type**, **order**, **cutoff frequency (Hz)**, **pass type** (lowpass / highpass)
- **Delay** in milliseconds
- **WAV loader** — replaces the impulse with a real audio file (mono or stereo, uses left channel)

## Usage

Run the notebook cell. The GUI opens at 1440 × 900 px with controls on the left and plots on the right.
Configure Channel 1 (top controls) and Channel 2 (middle controls), then observe how the filters interact.

Sample WAV files (white noise, pink noise, sine tone, square wave) are available in the original
[`audio-fx-analyzer`](https://github.com/soyDCAR/audio-fx-analyzer) repository for testing.

## Stack

`numpy` · `scipy` (butter, cheby1, cheby2, lfilter, fftfreq) · `matplotlib` · `tkinter`
