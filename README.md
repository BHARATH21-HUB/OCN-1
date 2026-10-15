# Experimental-verification-of-various-Fiber-losses--Propagation-Loss-Bend-Loss

## AIM
To measure propagation loss & bending losses for two different wavelengths in plastic Fiber using python.

---

## EQUIPMENTS REQUIRED
- Laptop/PC
- Google Colab

---

## PROGRAM
```py

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from IPython.display import display

# Propagation Loss values
length = [1, 3]
v660 = [1.60, 0.95]
v950 = [1.70, 1.30]

# Propagation Loss Tabulation
propagation = pd.DataFrame({
    "Fiber Length": ["1 m (660 nm)", "3 m (660 nm)",
                     "1 m (950 nm)", "3 m (950 nm)"],
    "Input Amplitude (V)": [2.0, 2.0, 2.0, 2.0],
    "Output Amplitude (V)": [1.60, 0.95, 1.70, 1.30]
})

print("PROPAGATION LOSS")
display(propagation)

# Attenuation calculation
for wavelength, voltage in [(660, v660), (950, v950)]:
    alpha = np.log(voltage[0] / voltage[1]) / (3 - 1)
    print(f"{wavelength} nm Attenuation = {alpha:.4f} Np/m")
    print(f"{wavelength} nm Attenuation = {8.686 * alpha:.4f} dB/m")

# Propagation Loss Graph
plt.plot(length, v660, 'o-', label="660 nm")
plt.plot(length, v950, 's-', label="950 nm")
plt.xlabel("Fiber Length (m)")
plt.ylabel("Output Amplitude (V)")
plt.title("Propagation Loss")
plt.grid()
plt.legend()
plt.show()

# Bending Loss Tabulation
diameter = [10, 8, 6, 4, 3, 2, 1]
output = [1.55, 1.50, 1.42, 1.28, 1.10, 0.82, 0.48]

bending = pd.DataFrame({
    "Bending Diameter (cm)": diameter,
    "Input Amplitude (V)": [2.0] * len(diameter),
    "Output Amplitude (V)": output
})

print("BENDING LOSS")
display(bending)

# Bending Loss Graph
plt.plot(diameter, output, 'o-')
plt.xlabel("Bending Diameter (cm)")
plt.ylabel("Output Amplitude (V)")
plt.title("Bending Loss at 660 nm")
plt.grid()
plt.show()
```

---

## TABULATION

### Propagation Loss
| Fiber Length | Input Amplitude (V)  | Output Amplitude (V)  |
|--------------|----------------------|-----------------------|
| 1 m (660 nm) |         2.0          |         1.60          |
| 3 m (660 nm) |         2.0          |         0.95          |
| 1 m (950 nm) |         2.0          |         1.70          |
| 3 m (950 nm) |         2.0          |         1.30          |


```
660 nm Attenuation = 0.2606 Np/m
660 nm Attenuation = 2.2640 dB/m
950 nm Attenuation = 0.1341 Np/m
950 nm Attenuation = 1.1651 dB/m
```

### Bending Loss
| Bending Diameter | Input Amplitude (V) | Output Amplitude (V) |
|------------------|----------------------|-----------------------|
|10                |2.0                   |1.55                   |
|8                 |2.0                   |1.50                   |
|6                 |2.0                   |1.42                   |
|4                 |2.0                   |1.28                   | 
|3                 |2.0                   |1.10                   |
|2                 |2.0                   |0.82                   |
|1                 |2.0                   |0.48                   |

---

## OUTPUT

<img width="537" height="599" alt="WhatsApp Image 2026-10-15 at 2 15 36 PM (1)" src="https://github.com/user-attachments/assets/4353387d-a226-476f-8e55-25fbcc35daea" />
<img width="533" height="500" alt="WhatsApp Image 2026-10-15 at 2 15 36 PM" src="https://github.com/user-attachments/assets/5f773e0b-132a-465f-98df-ac1a0bf5e1dc" />


## RESULT
- Propagation loss and bending losses for **660nm** and **950nm** wavelengths were measured.  
- Attenuation values compared and bending loss characteristics plotted.  
