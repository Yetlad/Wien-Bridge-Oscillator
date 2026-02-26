## Wien Bridge Oscillator – LTspice Simulation
# Overview

This project implements and analyses a Wien Bridge Oscillator using LTspice. The oscillator generates a low-distortion sine wave using a frequency-selective RC network and diode-based amplitude stabilization.

# Aim

Identify Wien bridge feedback network

Verify oscillation via transient simulation

Measure frequency using .meas and cursors

Compare theory vs simulation

Study gain impact on waveform distortion

Explain diode-based amplitude stabilization

# Circuit Parameters
.param R=10.2k
.param C=3n

# Expected frequency:

𝑓
0
=
1
2
𝜋
𝑅
𝐶
f
0
	​

=
2πRC
1
	​

𝑓
0
≈
5.20
𝑘
𝐻
𝑧
f
0
	​

≈5.20kHz
 # Simulation Command
.tran 0 20m 0 1u uic
 Frequency Measurement
.meas T20 when v(vout)=0 rise=20
.meas T21 when v(vout)=0 rise=21
.meas Fre param 1/(T21-T20)

View results via:

View → SPICE Error Log (Ctrl + L)

 # Results Summary
Case	Gain	Frequency	Observation
Below 3	<3	~5.2kHz	Oscillation dies
≈3	~3	~5.2kHz	Stable sine
Above 3	>3	~5.2kHz	Distorted / diode limiting
 # Theory
# Barkhausen Criteria

Loop phase shift = 360°

Loop gain = 1

Why Gain ≈ 3?

Wien network attenuation = 1/3
Amplifier gain must be 3 for sustained oscillation.

# Diode Stabilization

Diodes automatically adjust gain:

Small signal → gain > 3

Large signal → diodes conduct → gain reduces

Stable sine achieved

 # Key Learning Outcomes

Oscillator startup behaviour

Frequency measurement using .meas

Gain control effects

Nonlinear amplitude stabilization

Practical oscillator design
