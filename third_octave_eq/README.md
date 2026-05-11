# third_octave_eq

32-band graphic equalizer using 1/3-octave Butterworth band-pass filters with real-time FFT visualization.

## How it works

Each of the 32 ISO 266 center frequencies (20 Hz – 20 kHz) gets its own 4th-order Butterworth band-pass filter. Band limits are ±1/6 octave around each center frequency. Gain is applied per band and all bands are summed to produce the output signal.

## Usage

Run the notebook cell. A GUI will open:
1. Click **Cargar WAV** to load a `.wav` file.
2. Drag the faders (±30 dB per band) to apply equalization.
3. The FFT and waveform plots update on every fader move.

## Stack

`numpy` · `scipy` (butter, sosfilt, fft) · `matplotlib` · `tkinter`
