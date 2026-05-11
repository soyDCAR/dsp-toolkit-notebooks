# discrete_convolution

GUI calculator for discrete convolution Y[n] = Σ X[k]·h[n−k], comparing two manual implementations.

## Bug fix — magic number `min(11, ...)` removed

The original `convolucion_directa` function contained:

```python
# BEFORE (buggy) — silently capped sequences at 11 samples
X_values = [X[n-i] if ... else 0 for i in range(min(11, len(X)))]
Y_directo[n] = sum(h[i] * X_values[i] for i in range(min(len(h), len(X_values))))
```

The hardcoded `11` truncated the inner product to at most 11 terms, producing wrong results
whenever `h` had more than 11 coefficients. Fixed to iterate over the full length of `h`:

```python
# AFTER (fixed) — works for sequences of any length
X_values = [X[n-i] if (n-i) >= 0 and (n-i) < len(X) else 0 for i in range(N)]  # N = len(h)
Y_directo[n] = sum(h[i] * X_values[i] for i in range(N))
```

## Why manual instead of `numpy.convolve`?

`numpy.convolve` (and its FFT-based variant for long sequences) is the production choice. The manual
implementations here exist to make the summation algorithm explicit for educational purposes — you can
trace each term and verify the index arithmetic step by step.

## Methods

| Method | Description |
|--------|-------------|
| **Método Directo** | Slides the time-reversed h over X, computing the inner product at each position |
| **Método Suma** | Standard double-loop: `Y[n] += X[n-k] * h[k]` for all valid k |

Both must produce identical results for any input.

## Usage

Run the notebook cell. Enter `X[n]` and `h[n]` as comma-separated numbers and click **Calcular Convolución**.

## Stack

`numpy` · `tkinter`
