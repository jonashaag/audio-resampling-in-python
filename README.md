Comparison of audio resampling libraries. View the notebook: https://nbviewer.jupyter.org/github/jonashaag/audio-resampling-in-python/blob/master/Audio%20Resampling%20in%20Python.ipynb

### Best by quality

1. Good:
   - `scikit.samplerate`/`scikits-samplerate`/`samplerate`/`libsamplerate`
   - `librosa`/`resampy` (`"kaiser_best"`)
   - `julius`
3. Acceptable:
   - `nnresample`
   - `lilfilter`
   - `torchaudio` (`transforms.Resample` + `resample_waveform`)
   - `librosa`/`resampy` (`"kaiser_fast"`)
5. Bad:
   - `scipy.signal.resample`

### Best by speed

Downsampling from 48 kHz to 44.1 kHz.

| Library | Time on CPU | Time on GPU |
| - | - | - |
| `soxr` | 1.16 ms | no support |
| `scipy.signal.resample` | 2.42 ms | no support |
| `lilfilter` | 4.23 ms | ? |
| `torchaudio` (`transforms.Resample`) | 9.98 ms | ? |
| `torchaudio` (`resample_waveform`) | 10 ms | ? |
| `resampy` (`"kaiser_fast"`) | 10.5 ms | no support |
| `nnresample` | 16 ms | no support |
| `julius` | 16.2 ms | ? |
| `resampy` (`"kaiser_best"`) | 44.8 ms | no support |
| `scikits.samplerate` | 75.5 ms | no support |
| `samplerate` | 76.8 ms | no support |
