**Abstract**
Analog in-memory computing (IMC) crossbar arrays are emerging as energy-efficient accelerators for edge AI inference. A widely held assumption is that analog computation is inherently more side-channel resistant than digital designs — since there are no discrete bit transitions to leak information.

This notebook challenges that assumption.

Using the open-source SkyWater SKY130 130 nm foundry PDK and Ngspice 42, we demonstrate that the total supply current of a 4×4 resistive crossbar IMC array during matrix-vector multiplication is near-perfectly correlated with the Hamming weight of the input vector (Pearson ρ = 0.998, p < 10⁻¹⁷). This constitutes a practical power side-channel attack that leaks private input data.

We further show the attack survives down to SNR = 3.0 dB, that passive dummy-column countermeasures are completely ineffective due to NMOS nonlinearity, that the vulnerability is invariant across all five SKY130 process corners, and that it scales to 8×8 arrays. We also demonstrate a weight-extraction attack showing that secret model weights are recoverable from power measurements alone.

**Result	Value** 
PDK	SkyWater SKY130 130 nm (real foundry model)
Simulator	Ngspice 42
Side-channel correlation (4×4, TT)	ρ = 0.9979
p-value	5.27 × 10⁻¹⁸
Attack viable down to SNR	3.0 dB
Passive countermeasure effectiveness	0%
Corner invariance (TT/FF/SS/SF/FS)	ρ range = 0.0001
8×8 array correlation	ρ = 0.9976
