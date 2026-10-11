# Design-and-Simulation-of-a-CMOS-Low-Dropout-Voltage-Regulator-LDO-
Transistor-level design and simulation of a 45 nm CMOS PMOS-pass LDO in Cadence Virtuoso, comparing Miller and RC lead-lag compensation for stability, PSRR, noise, and transient response.
# Low-Dropout Voltage Regulator (LDO) Design Using Cadence Virtuoso

## Overview

This project explores the transistor-level design and simulation analysis of a conventional Low-Dropout Voltage Regulator (LDO) using 45 nm CMOS technology. The design consists of a five-transistor Operational Transconductance Amplifier (OTA) serving as the error amplifier, a PMOS pass transistor, a resistive feedback network, and a load.

The regulator is designed to provide a stable **0.9 V output from a 1.2 V supply**, using a 0.75 V reference voltage. The project investigates the impact of two frequency-compensation techniques—Miller compensation and RC lead-lag compensation—on loop stability, Power Supply Rejection Ratio (PSRR), output noise, and transient response.

Circuit schematics and simulation analyses are performed using Cadence Virtuoso.

## Objectives

- Design a conventional PMOS-pass LDO using 45 nm CMOS technology.
- Develop a five-transistor OTA for error amplification and feedback regulation.
- Establish the required DC operating points for the amplifier and pass transistor.
- Investigate loop stability using Miller and RC lead-lag compensation.
- Evaluate DC gain, phase margin, PSRR, output noise, and transient response.
- Analyze mismatch-induced offset using Monte Carlo simulation.
- Compare compensation techniques to understand their impact on regulator performance.

## Design Specifications

| Parameter | Specification |
|---|---|
| CMOS technology | 45 nm |
| Input supply voltage | 1.2 V |
| Reference voltage | 0.75 V |
| Regulated output voltage | 0.9 V |
| Load current range | 5–30 mA |
| Load capacitance | 200 pF |
| Error amplifier | Five-transistor OTA |
| Pass device | PMOS |
| Compensation techniques | Miller and RC lead-lag |
| Circuit design and simulation | Cadence Virtuoso |

## LDO Architecture

The regulator consists of the following functional blocks:

### 1. Error Amplifier

A five-transistor OTA compares the reference voltage with the feedback voltage derived from the regulated output. The resulting error signal controls the PMOS pass transistor to maintain the target output voltage.

### 2. PMOS Pass Transistor

The PMOS transistor acts as the series pass element between the input supply and the output. Its gate voltage is adjusted by the error amplifier to regulate the output under changing load conditions.

### 3. Resistive Feedback Network

A resistor divider samples the output voltage and generates the feedback voltage. The feedback ratio determines the regulated output voltage relative to the reference.

### 4. Compensation Network

The compensation network shapes the loop gain and phase response to improve closed-loop stability and reduce undesirable transient oscillations.

### 5. Load Network

The output load is modeled using a load current and a 200 pF load capacitor to evaluate the regulator across its specified operating range.

## Compensation Techniques

### Miller Compensation

Miller compensation uses a capacitor connected between the relevant amplifier/pass-device nodes to modify the effective capacitance and separate the dominant and non-dominant poles.

The technique is evaluated for its effect on loop stability, phase margin, PSRR, output noise, and settling time.

### RC Lead-Lag Compensation

RC lead-lag compensation introduces a resistor-capacitor network to create a pole-zero pair. The component values are selected to shape the frequency response and improve stability.

The report uses a compensation resistance of 300 Ω and a compensation capacitance of 20 pF for its reported final comparison.

## Simulation and Analysis

The project report covers the following analyses in Cadence Virtuoso:

- **DC operating-point analysis:** Evaluates transistor biasing and operating regions across the load-current range.
- **AC analysis:** Examines frequency response and PSRR.
- **Stability analysis (STB):** Evaluates loop gain and phase margin.
- **Transient analysis:** Examines output settling and response to load changes.
- **Noise analysis:** Evaluates the output noise contribution from the amplifier and feedback network.
- **Monte Carlo analysis:** Investigates mismatch-induced feedback offset and its statistical variation over 500 samples.

## Reported Results

The following values are taken from the project report and are presented as reported simulation results.

| Metric | RC Lead-Lag | Miller |
|---|---:|---:|
| Minimum DC gain | 43.22 dB | 43.22 dB |
| Minimum phase margin | 60.34° | 99.23° |
| PSRR at DC | 41.14 dB | 41.14 dB |
| PSRR at 1 MHz | 35.73 dB | 15.33 dB |
| PSRR at 1 GHz | 13.13 dB | 8.24 dB |
| Worst-case PSRR | 8.89 dB | 1.44 dB |
| Integrated output noise (1 MHz–10 GHz) | 191.7 µV² | 104 µV² |
| Settling time (99%) | 16.29 ns | 20.05 ns |

### Monte Carlo Analysis

The report evaluates mismatch-induced offset using 500 simulation samples. At a transistor-dimension scaling factor of four, the reported feedback offset statistics are:

- Mean offset: approximately 770 µV.
- Standard deviation: approximately 1.513 mV.

The reported results illustrate how transistor sizing affects mismatch sensitivity.

## Key Observations

- Both compensation techniques achieve the reported minimum DC loop gain of 43.22 dB.
- Miller compensation provides a higher reported minimum phase margin.
- RC lead-lag compensation provides better reported PSRR at 1 MHz, 1 GHz, and under the worst-case condition.
- Miller compensation has lower reported integrated output noise.
- RC lead-lag compensation achieves a shorter reported 99% settling time.
- Compensation selection requires balancing stability, PSRR, noise, and transient performance.

## Repository Structure

```text
ldo-design-cadence-virtuoso/
├── README.md
├── schematics/
│   ├── ldo_rc_compensation.png
│   ├── ldo_miller_compensation.png
│   └── five_transistor_ota.png
├── simulations/
│   ├── dc_analysis/
│   ├── ac_psrr_analysis/
│   ├── stability_analysis/
│   ├── transient_analysis/
│   ├── noise_analysis/
│   └── monte_carlo_analysis/
├── results/
│   └── compensation_comparison.md
└── docs/
    └── design_report.pdf
```

*This is a suggested structure. Include only files and results that you have created, reproduced, or are permitted to redistribute.*

## Tools and Technologies

- Cadence Virtuoso
- 45 nm CMOS device models
- Analog circuit design and transistor-level simulation
- AC, DC, STB, transient, noise, and Monte Carlo analyses

## Applications

LDO regulators are commonly used for:

- On-chip power management and voltage regulation.
- Low-noise supply rails for analog and mixed-signal circuits.
- System-on-Chip (SoC) power delivery.
- Local voltage regulation for sensitive integrated circuits.

## Future Improvements

Potential extensions include:

- Improving PSRR across a wider frequency range.
- Optimizing quiescent current and dropout performance.
- Investigating load-transient response over a broader load range.
- Performing process-voltage-temperature (PVT) corner analysis.
- Evaluating layout parasitics and post-layout performance.
- Comparing alternative error-amplifier and pass-device architectures.

## Acknowledgment and Attribution

This repository is intended for educational exploration of analog CMOS circuit design and LDO compensation. The original project report is titled *Design Procedure of a Conventional Low-Dropout Circuit* by Muhammad Aldacher.

Any reused schematics, circuit implementations, text, or simulation data should be attributed to the original author and redistributed only under the applicable license or with permission.
