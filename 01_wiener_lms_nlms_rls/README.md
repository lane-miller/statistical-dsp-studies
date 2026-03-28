# 01 — Adaptive Filtering

**Dataset:** Wrist PPG During Exercise (PhysioNet WRIST 1.0.0) — subject 3, walking
**Filters:** Wiener (time domain), LMS, NLMS, RLS
**Problem:** PPG motion artifact removal using accelerometer as reference signal
**Architecture:** Two-channel adaptive noise cancellation — accelerometer as x(n), corrupted PPG as d(n), cleaned PPG as e(n)

## Results


| Method           | HR (bpm) | Error vs ECG |
| ---------------- | -------- | ------------ |
| ECG ground truth | 99.0     | —            |
| LMS              | 96.7     | -2.3         |
| RLS              | 94.8     | -4.2         |
| NLMS             | 94.3     | -4.7         |
| Wiener           | 92.2     | -6.8         |
| Raw PPG          | 88.4     | -10.6        |


## Key Takeaways

- All adaptive methods improve HR estimation over raw PPG (88.4 bpm)
- LMS performed best on this dataset: 96.7 bpm vs 99.0 bpm ECG ground truth
    - NLMS and RLS both comparable
- Wiener batch estimate weakest "adaptive" result
    - Fixed filter suboptimal for non-stationary artifact
- LMS outperforming NLMS and RLS could be because of steady-state walking
    - normalization and fast convergence provide little advantage over well-tuned fixed step size
- Linear adaptive filtering limited: CANNOT remove nonlinear accel artifacts

## References

1. Jarchi, D. & Casson, A.J. (2017). Description of a Database Containing Wrist PPG 
   Signals Recorded during Physical Exercise with Both Accelerometer and Gyroscope 
   Measures of Motion. *Data*, 2(1), 1. https://doi.org/10.3390/data2010001

2. Goldberger, A. et al. (2000). PhysioBank, PhysioToolkit, and PhysioNet: Components 
   of a new research resource for complex physiologic signals. *Circulation*, 101(23), 
   e215–e220. https://doi.org/10.1161/01.CIR.101.23.e215


3. Shafiq, G. et al. (2019). Performance Comparison of Variants of LMS Algorithms for 
   Motion Artifact Removal in PPG Signals During Physical Activities. 
   *Biomedical Research*, 30(5). https://doi.org/10.26717/BJSTR.2019.13.002485

4. Ye, Y. et al. (2019). Removal of Motion Artifacts in Photoplethysmograph Sensors 
   during Intensive Exercise for Accurate Heart Rate Calculation. *Sensors*, 19(16), 3595. https://doi.org/10.3390/s19163595

