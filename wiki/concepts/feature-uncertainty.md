---
type: concept
status: active
sources: [summary-eagle]
updated: 2026-09-02
---

# Feature uncertainty

Features are continuous; you cannot "sample a feature" the way you sample a token. After token "I", both "am" and "always" are legal, and they induce **different** next features. Predicting \(f_{t+1}\) from \(f_t\) alone is ill-posed.

EAGLE's fix: also input \(t_{t+1}\) (token advanced by one step — the sampling outcome). Predict \(f_{\text{always}}\) from \((f_I, t_{\text{always}})\). Ablation: 1.9× → 2.8× on Vicuna-7B MT-bench T=0.

Medusa's independent heads have a related ambiguity (which token actually landed at offset k-1?). [[hydra]] attacks that with sequential dependence.
