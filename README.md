# fNIRS
### Emotion Detection

### 1. Detecting and rejecting low quality channels (SCI 사용)

- **Scalp coupling index (SCI)
T**ests for negative correlation in the heartbeat’s frequency range (0.7–1.5 Hz) between channels measuring activity at different wavelengths in the same area.

Low SCI indicates poor coupling; therefore, channels with SCI below 0.8 were interpolated by taking the average of the nearest adequate channels at the same wavelength.

```python
sci = scalp_coupling_index(raw_od)         # shape: (n_channels,)
bad_idx = [i for i, v in enumerate(sci) if v < 0.5]  # 임계값 예: 0.5
raw_od.info['bads'] = [raw.ch_names[i] for i in bad_idx]

```

### 2. Optical density (OD)

### 3. Removing motion artifacts (TDDR 사용)

Applying the TDDR to OD signal

- **Temporal derivative distribution repair (TDDR)**
    
    motion correction procedure, which effectively removes spike artifacts without any user-specified parameters.
    

### 4. Converting into HbO & HbR concentrations

- **Modified Beer-Lambert law**

### 5. FIR Band-pass filtering (0.01–0.1 Hz)

The low-pass component (0.1 Hz) aimed to remove physiological noise such as heartbeat signals from the haemoglobin concentrations,
The high-pass component (0.01 Hz) eliminated slow drifts. 

### 6. Segmenting into epochs

Finally, the data were segmented into epochs, each consisting of a 12-second post-stimulus segment and a preceding 5-second baseline interval for baseline correction
