# 02 — Kalman, EKF, UKF

**System:** Simple pendulum (simulated)
**Filters:** Standard Kalman, Extended Kalman (EKF), Unscented Kalman (UKF)
**Problem:** State estimation of pendulum angle and angular velocity from noisy angle observations
**Architecture:** Hidden state [θ, θ_dot], observed θ only — velocity inferred through dynamics model

## Results — Velocity RMSE (deg/s)

| θ₀ (deg) | KF | EKF | UKF |
|---|---|---|---|
| 15 | 5.71 | 6.61 | 6.73 |
| 30 | 6.38 | 6.24 | 5.86 |
| 45 | 13.76 | 4.93 | 5.23 |
| 60 | 27.43 | 5.17 | 5.09 |

## Key Takeaways

- UKF and EKF performance comparable on this problem
    - expected where first order Taylor series approx (EKF) performs adequately
- Both nonlinear methods dramatically outperform standard Kalman at large angles
- Where UKF advantage would be more pronounced:
    - stronger nonlinearity 
    - higher noise
    - Jacobian computation difficult