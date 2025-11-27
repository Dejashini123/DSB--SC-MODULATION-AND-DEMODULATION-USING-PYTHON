# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message
 __Program__:
```import numpy as np
import matplotlib.pyplot as plt
Ac = 2
fc = 7000
Am = 5
fm = 700
fs = 70000
t = np.arange(0, 2/fm, 1/fs)
Wm = 2 * np.pi * fm
Wc = 2 * np.pi * fc
Em = Am * np.sin(Wm * t)
Ec = Ac * np.sin(Wc * t)
Edsbsc = ((Am / 2) * np.cos((Wc - Wm) * t)) - ((Am / 2) * np.cos((Wc + Wm) * t))
plt.figure(figsize=(10, 6))
plt.subplot(3, 1, 1)
plt.plot(t, Em)
plt.grid()
plt.subplot(3, 1, 2)
plt.plot(t, Ec)

plt.grid()
plt.subplot(3, 1, 3)
plt.plot(t, Edsbsc)
plt.grid()
plt.tight_layout()
plt.show()
```
### Tabulation:
   <img width="899" height="1599" alt="image" src="https://github.com/user-attachments/assets/0d3f3488-3af2-47e4-bdd6-b66549c90df3" />


 __Output__:
   <img width="987" height="587" alt="image" src="https://github.com/user-attachments/assets/721fe21e-c1a3-43bd-b338-fcd38cb00585" />


 __Result__:
![WhatsApp Image 2025-11-27 at 10 05 22 PM](https://github.com/user-attachments/assets/844faf5f-9f4e-47fa-9bfa-539ecdd08c8b)
