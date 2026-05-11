# DSP Toolkit Notebooks

Una colección de herramientas interactivas en Python para el análisis de señales digitales y acústica física. Cada notebook contiene una GUI construida con `tkinter` y `matplotlib` lista para usar sin configuración adicional.

---

## Herramientas incluidas

| # | Notebook | Descripción |
|---|----------|-------------|
| 1 | [`wav-speed-shifter`](notebooks/wav-speed-shifter.ipynb) | Acelera o desacelera archivos WAV por remuestreo (afecta pitch). |
| 2 | [`wav-delta-visualizer`](notebooks/wav-delta-visualizer.ipynb) | Calcula y grafica la Primera Derivada Discreta (Forward Difference) de una señal WAV. |
| 3 | [`discrete-convolution-calc`](notebooks/discrete-convolution-calc.ipynb) | Calculadora de convolución discreta: método directo vs. método por suma. |
| 4 | [`radiation-pattern-sim`](notebooks/radiation-pattern-sim.ipynb) | Simula y grafica patrones de radiación polares (monopolo, dipolo, tripolo, cuadripolo). |
| 5 | [`acoustic-horn-plotter`](notebooks/acoustic-horn-plotter.ipynb) | Grafica el perfil y la revolución 3D de bocinas cónicas, exponenciales, catenoidales e hiperbólicas. |
| 6 | [`graphic-equalizer-fft`](notebooks/graphic-equalizer-fft.ipynb) | Ecualizador de 32 bandas (tercios de octava) con visualización FFT y forma de onda en tiempo real. |

---

## Instalación

```bash
pip install numpy matplotlib scipy
```

> `tkinter` viene incluido con Python en Windows y macOS. En Linux:
> ```bash
> sudo apt install python3-tk
> ```

### Requisitos por herramienta

| Herramienta | numpy | matplotlib | scipy |
|-------------|:-----:|:----------:|:-----:|
| wav-speed-shifter | ✓ | — | ✓ |
| wav-delta-visualizer | ✓ | ✓ | ✓ |
| discrete-convolution-calc | ✓ | — | — |
| radiation-pattern-sim | ✓ | ✓ | — |
| acoustic-horn-plotter | ✓ | ✓ | — |
| graphic-equalizer-fft | ✓ | ✓ | ✓ |

---

## Uso rápido

Abre cada notebook en Jupyter Lab / Notebook y ejecuta la celda principal. Se abrirá una ventana GUI independiente.

```bash
jupyter lab notebooks/discrete-convolution-calc.ipynb
```

---

## Descripción de cada herramienta

### 1. WAV Speed Shifter
Procesa archivos `.wav` modificando la tasa de muestreo mediante decimación (×2) o interpolación por repetición (÷2). **Importante:** al operar sobre las muestras directamente (sin Phase Vocoder), el cambio de velocidad altera también el tono de la señal una octava hacia arriba o hacia abajo.

### 2. WAV Delta Visualizer
Aplica la diferencia hacia adelante (`np.diff`) sobre las primeras 30 muestras de un archivo WAV y muestra el resultado como un stem plot. La diferencia hacia adelante `Δx[n] = x[n+1] − x[n]` es la aproximación discreta de la primera derivada de la señal.

### 3. Discrete Convolution Calculator
Implementa la convolución discreta `Y[n] = Σ X[k]·h[n−k]` mediante dos métodos independientes:
- **Método directo:** desliza la respuesta al impulso h invertida sobre X.
- **Método por suma:** itera sobre todos los términos de la suma de convolución.

Ambos métodos aceptan secuencias de longitud arbitraria. Se usa implementación manual (en lugar de `numpy.convolve`) para mostrar el mecanismo algorítmico de forma explícita con fines educativos.

### 4. Radiation Pattern Simulator
Calcula y grafica en coordenadas polares los patrones de radiación acústica para cinco configuraciones de fuentes puntuales basadas en la formulación del cuadripolo acústico:
- **Monopolo:** radiación omnidireccional uniforme.
- **Dipolo:** patrón en figura de ocho.
- **Tripolo ±:** asimetría direccional por combinación de tres fuentes.
- **Cuadripolo:** superposición con pesos fraccionarios (7/8, 1/4, 3/4).

### 6. Graphic Equalizer FFT
Ecualizador gráfico de **32 bandas de tercio de octava** (20 Hz – 20 kHz, norma ISO 266). Cada banda usa un filtro Butterworth de orden 4 en formato SOS (segunda sección de orden, numéricamente estable). Los faders aplican ganancia de ±30 dB en tiempo real y las gráficas se actualizan en cada movimiento:
- **Panel superior:** espectro de magnitud en dB (escala logarítmica), original vs. filtrado.
- **Panel inferior:** comparación de formas de onda en el dominio del tiempo.

### 5. Acoustic Horn Plotter
Visualiza el perfil de área transversal S(x) y su revolución 3D para cuatro leyes de expansión de bocina:
- **Cónica:** `S(x) = ST·(x/x₀)²`
- **Exponencial:** `S(x) = ST·e^(mx)` — mayor ancho de banda de paso.
- **Catenoidal:** `S(x) = ST·cosh²(mx/2)`
- **Hiperbólica:** `S(x) = ST·[cosh(mx/2) + M·sinh(mx/2)]²` con `0 < M < 1`.

---

## Mejoras futuras

- [ ] **Time-Stretching real (Phase Vocoder):** cambio de velocidad sin alteración de pitch en `wav-speed-shifter`, usando análisis STFT y resíntesis con corrección de fase.
- [ ] **Visualización extendida en `wav-delta-visualizer`:** segunda derivada discreta, espectrograma de la señal completa.
- [ ] **Convolución con señales reales en `discrete-convolution-calc`:** cargar X[n] y h[n] desde archivos `.wav` o `.csv`.
- [ ] **Normalización dB en `radiation-pattern-sim`:** mostrar la escala en dB SPL y añadir curvas de nivel.
- [ ] **Frecuencia de corte en `acoustic-horn-plotter`:** calcular y mostrar `f_c = mc/(4π)` para cada tipo de bocina.
- [ ] **Exportar audio ecualizado en `graphic-equalizer-fft`:** guardar la señal filtrada como archivo `.wav`.
- [ ] **Tests unitarios:** verificar resultados de convolución y diferencia discreta contra referencias analíticas conocidas.

---

## Autor

**Dilan Acosta**

## Licencia

MIT — ver [LICENSE](LICENSE).
