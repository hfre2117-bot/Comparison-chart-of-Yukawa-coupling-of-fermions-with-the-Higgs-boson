# Comparison-chart-of-Yukawa-coupling-of-fermions-with-the-Higgs-boson
Comparison chart of Yukawa coupling of fermions with the Higgs boson
import numpy as np
import matplotlib.pyplot as plt

# مقدار VEV هیگز (GeV)
v = 246  

# جرم فرمیون‌ها (GeV)
fermions = {
    "Electron": 0.000511,
    "Muon": 0.105,
    "Tau": 1.776,
    "Up quark": 0.0022,
    "Charm quark": 1.27,
    "Top quark": 173
}

# محاسبه کوپلینگ یوکاوا نظری
yukawa = {f: np.sqrt(2)*m/v for f, m in fermions.items()}

# داده‌های تجربی نسبی (نرمال‌شده به مدل استاندارد ≈ 1)
experimental_ratio = {
    "Electron": 1.1,
    "Muon": 0.98,
    "Tau": 1.05,
    "Up quark": 0.9,
    "Charm quark": 1.02,
    "Top quark": 1.01
}

# آماده‌سازی داده‌ها
names = list(fermions.keys())
y_values = [yukawa[n] for n in names]
exp_values = [yukawa[n] * experimental_ratio[n] for n in names]

# رسم نمودار
plt.figure(figsize=(10,6))

plt.bar(names, y_values, alpha=0.6, label="SM Prediction")
plt.scatter(names, exp_values, color='red', zorder=3, label="Experimental")

plt.yscale("log")
plt.ylabel("Yukawa Coupling")
plt.title("Fermion-Higgs Yukawa Coupling Comparison")
plt.legend()
plt.xticks(rotation=45)
plt.grid(True, which="both", linestyle="--", alpha=0.5)

plt.tight_layout()
plt.show()
