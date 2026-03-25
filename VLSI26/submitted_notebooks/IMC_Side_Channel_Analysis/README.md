# Power Side-Channel Vulnerability in Analog In-Memory Computing Crossbars

## Abstract

Analog in-memory computing (IMC) crossbar arrays are emerging as energy-efficient accelerators for edge AI inference. A widely held assumption is that analog computation is inherently more side-channel resistant than digital designs, since there are no discrete bit transitions to leak information.

This work challenges that assumption.

Using the open-source SkyWater SKY130 130 nm foundry PDK and Ngspice 42, we demonstrate that the total supply current of a 4×4 resistive crossbar IMC array during matrix-vector multiplication is nearly perfectly correlated with the Hamming weight of the input vector (Pearson correlation coefficient ρ = 0.998, p < 10⁻¹⁷). This establishes a practical power side-channel attack capable of leaking private input data.

Unlike prior work that primarily focuses on digital accelerators or simplified analytical models, this study provides the first SPICE-level, foundry-validated demonstration of power side-channel leakage in analog IMC crossbars using the SKY130 PDK, including robustness across process corners and noise conditions.

We further show that:
- The attack remains viable down to a signal-to-noise ratio (SNR) of 3.0 dB  
- Passive dummy-column countermeasures are ineffective due to NMOS nonlinearity  
- The vulnerability persists across all SKY130 process corners (TT, FF, SS, SF, FS)  
- The leakage behavior scales to larger arrays (validated on 8×8)  
- Secret model weights can be extracted using power measurements alone  

These findings challenge the prevailing assumption of inherent security in analog AI hardware, highlighting an urgent need for dedicated side-channel-aware design methodologies in next-generation IMC-based edge accelerators.

---

## Key Results

| Metric | Value |
|------|------|
| **PDK** | SkyWater SKY130 130 nm (real foundry model) |
| **Simulator** | Ngspice 42 |
| **Side-channel correlation (4×4, TT)** | ρ = 0.9979 |
| **p-value** | 5.27 × 10⁻¹⁸ |
| **Attack viability (minimum SNR)** | 3.0 dB |
| **Passive countermeasure effectiveness** | 0% |
| **Corner invariance (TT/FF/SS/SF/FS)** | Δρ ≈ 0.0001 |
| **8×8 array correlation** | ρ = 0.9976 |

---

## Key Takeaways

- Analog IMC is **not inherently side-channel secure**
- Power leakage directly reveals **input Hamming weight**
- Traditional passive defenses are **ineffective**
- Vulnerability is **robust across noise, process variation, and scaling**
- Both **inputs and weights are at risk**

---

## Keywords

Analog In-Memory Computing, Side-Channel Attack, Power Analysis, Crossbar Arrays, SKY130, Ngspice, Hardware Security, Edge AI
