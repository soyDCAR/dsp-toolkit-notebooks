# wav_speed_shifter

Speeds up or slows down a `.wav` file by resampling (sample decimation / repetition).

## Important — pitch is affected

This tool changes speed **by operating on the raw samples**, not with a phase vocoder:

| Operation | Method | Effect on pitch |
|-----------|--------|-----------------|
| Accelerate ×2 | Keep every other sample (`data[::2]`) | +1 octave |
| Decelerate ×0.5 | Repeat each sample twice (`np.repeat`) | −1 octave |

For pitch-invariant time-stretching, a Phase Vocoder (STFT-based) would be required — that is listed as a future improvement in the main README.

## Usage

Run the notebook cell. A GUI will open:
1. Click **Cargar Archivo** and select a `.wav`.
2. Click **Acelerar a x2** or **Desacelerar a 0.5x**.
3. Output files `audio_acelerado.wav` / `audio_desacelerado.wav` are saved in the working directory.

## Stack

`numpy` · `scipy.io.wavfile` · `tkinter`
