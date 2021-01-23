Comparison of audio resampling libraries. View the notebook: https://nbviewer.jupyter.org/github/jonashaag/audio-resampling-in-python/blob/master/Audio%20Resampling%20in%20Python.ipynb

### Best by quality

1. Very good: `scikit.samplerate`/`scikits-samplerate`/`samplerate`/`libsamplerate`, `librosa`/`resampy`
2. Good: `julius`
3. Acceptable:  `lilfilter`, `torchaudio.transforms.Resample`
3. Bad: `scipy.signal.resample`

### Best by speed

Downsampling from 48 kHz to 44.1 kHz.

| Library | Time on CPU | Time on GPU |
| - | - | - |
| `lilfilter` | 3.22 ms ± 378 µs | ? |
| `scipy.signal.resample` | 4.41 ms ± 992 µs | no support |
| `julius` | 15.5 ms ± 2.57 ms<sup>1</sup>  | ? |
| `resampy` | 15.1 ms ± 359 µs (`"kaiser_fast"`) | no support |
| `julius` | 22.1 ms ± 4.84 ms | ? |
| `resampy` | 75.5 ms ± 3.75 ms (`"kaiser_best"`) | no support |
| `torchaudio` | 110 ms ± 8.31 ms | ? |
| `scikits.samplerate` | 145 ms ± 3.83 ms | no support |
| `samplerate` | 155 ms ± 25.7 ms | no support |

<small>
<sup>1</sup>Upsampling 48 kHz -> 96 kHz. Julius' performance improves with large GCD(original sr, target sr). For GCD(48000, 44100) = 300, GCD(48000, 96000) = 48000.
</small>
