---
id: system-overview
title: System Overview – IoT Guitar FX Processor (ESP32)
sidebar_label: System Overview
---

# **IoT Guitar FX Processor – System Overview**
This document provides a complete technical description of the IoT Guitar FX Processor developed using an ESP32 microcontroller, an analog front-end, DSP pipeline, and a 7W Class-D amplifier.

It serves as **technical documentation**, not a monograph.  
Use it as a reference for hardware, firmware, architecture, diagrams, and system behavior.

---

# **1. Project Summary**
The IoT Guitar FX Processor is a hybrid analog–digital device capable of:

- capturing guitar audio through a high-impedance preamp,  
- converting it using high-fidelity I²S ADC,  
- processing audio in real time (DSP on ESP32),  
- simulating cabinets with IR convolution,  
- outputting the processed audio via DAC into a 7W amplifier,  
- integrating with IoT features (Wi-Fi/BLE),  
- storing presets and IRs on SD-card,  
- providing UI through OLED + encoder + potentiometers.

This system combines **embedded audio processing**, **IoT control**, and **analog circuitry** in a compact hardware design.

---

# **2. System Architecture**

The complete architecture is shown below:

### **System Architecture**
![System Architecture](../arquitetura.png)

### Core Components
| Module | Description |
|--------|-------------|
| ESP32 WROOM | Main processor (DSP + IoT + UI) |
| PCM1802 | External ADC with I²S |
| PCM5102A | External DAC |
| TL072 | High-impedance guitar preamplifier |
| PAM8403 (7W) | Class-D output amplifier |
| OLED Display | UI visualization |
| Encoder + Pots | Parameter control |
| SD-card | Presets and IR storage |

---

# **3. Signal Path**
The internal signal chain includes analog and digital stages.

### **Signal Path Diagram**
![Signal Path](../signal%20path.png)

### Processing Stages
1. **High-impedance preamp**  
2. **Soft-clipping protection**  
3. **ADC conversion via I²S (48 kHz)**  
4. **DSP pipeline on ESP32:**  
   - Noise Gate  
   - EQ (biquad filters)  
   - Distortion (waveshaping)  
   - IR convolution (FFT)  
5. **DAC output via I²S**  
6. **7W amplifier → Speaker / Headphones**

---

# **4. Hardware Documentation**

### 4.1 Complete Hardware Schematic
![Schematic](../squematic.png)

Includes:
- Analog preamp  
- ADC/DAC interfaces  
- Power stages  
- Amplifier module  
- OLED + UI controls  

---

### 4.2 Amplifier Circuit
Used for driving speakers or monitoring headphones.

![Amplifier](../circut.png)

Key features:
- 7W output  
- High efficiency (>80%)  
- Clean 5V operation  
- Compatible with DAC line level  

---

# **5. Firmware & DSP Overview**

The ESP32 handles:

### **5.1 Real-Time DSP**
- I²S duplex audio streaming  
- Biquad filtering (EQ)  
- Waveshaping distortion  
- IR convolution (partitioned FFT)  
- Sample mixing & limiting  

### Example Biquad Equation
```cpp
y[n] = a0*x[n] + a1*x[n-1] + a2*x[n-2]
     - b1*y[n-1] - b2*y[n-2];

5.2 IoT Features

Wi-Fi UDP audio streaming

BLE remote control

Bluetooth A2DP output

Preset synchronization (optional Firebase)

5.3 SD-Card Storage

Stores:

IR files (.wav/.pcm)

Presets

Configuration files

6. User Interface

The system UI is based on:

1.3'' OLED display

Rotary encoder (push + rotation)

Two potentiometers (Gain / Tone)

Menu Structure

Input Gain

Equalizer

IR Selection

Amp Model

Output Volume

System Settings

7. Performance Metrics
Metric	Result
DSP Latency	11–13 ms
Bluetooth Audio Latency	~35 ms
ADC/DAC SNR	~90 dB
Power Draw	310–450 mA
Max IR Length	~2048 taps
Preamp Gain	+26 dB
8. Repository Structure
2025-1A-T01-G06-PUBLICO/
│
├── arquitetura.png
├── signal path.png
├── squematic.png
├── circut.png
│
└── Artigo/
    ├── monografia.md
    └── artigo.md

9. Future Improvements

Recommended enhancements:

ML-based amp modeling

Convolution reverb

Lightweight VST hosting (USB mode)

Full mobile app

BLE-MIDI integration

Rechargeable battery module

Larger display (TFT)

10. Credits

Developed by Gabriel Pascoli Terezo
Engineering in Computer Science – Inteli
Advisor: Prof. Rafael Matsuyama