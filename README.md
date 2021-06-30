Comparison of audio resampling libraries. View the notebook: https://nbviewer.jupyter.org/github/jonashaag/audio-resampling-in-python/blob/master/Audio%20Resampling%20in%20Python.ipynb

### Best by quality

1. Good:
   - `scikit.samplerate`/`scikits-samplerate`/`samplerate`/`libsamplerate`
   - `librosa`/`resampy` (`"kaiser_best"`)
   - `julius`
3. Acceptable:
   - `nnresample`
   - `lilfilter`
   - `torchaudio` (`transforms.Resample` + `functional.resample`)
   - `librosa`/`resampy` (`"kaiser_fast"`)
5. Bad:
   - `scipy.signal.resample`

### Best by speed

Downsampling from 48 kHz to 44.1 kHz.

| Library | Time on CPU | Time on GPU |
| - | - | - |
| `torchaudio` (`transforms.Resample`) | 0.977 ms | ? |
| `soxr` | 1.23 ms | no support |
| `scipy.signal.resample` | 1.94 ms | no support |
| `lilfilter` | 5.02 ms | ? |
| `torchaudio` (`functional.resample`) | 10.7 ms | ? |
| `julius` | 12.5 ms | ? |
| `resampy` (`"kaiser_fast"`) | 12.7 ms | no support |
| `nnresample` | 19.2 ms | no support |
| `resampy` (`"kaiser_best"`) | 61.6 ms | no support |
| `scikits.samplerate` | 84.6 ms | no support |
| `samplerate` | 85.7 ms | no support |
