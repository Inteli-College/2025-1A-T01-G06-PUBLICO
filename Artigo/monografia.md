IoT Audio Processing Device Using ESP32
Full Monograph — Markdown Version

Author: Gabriel Pascoli Terezo
Institution: Inteli – Institute of Technology and Leadership
Advisor: Prof. Rafael Matsuyama
Year: 2025

Abstract

This monograph presents the development of an IoT-based digital audio processing device using an ESP32 microcontroller. The system captures musical signals (especially electric guitar), processes them through embedded DSP (including EQ, distortion, and Impulse Response convolution), and outputs real-time audio via a 7 W analog amplifier.

The device integrates:

an analog preamplifier,

high-fidelity ADC/DAC via I²S,

ESP32 DSP in C/C++,

SD-card storage for IR files,

IoT connectivity,

a class-D audio amplifier,

an OLED interface + knobs and footswitch.

Table of Contents

Introduction

Literature Review

Theoretical Foundation

Methodology

System Architecture

Hardware Design

DSP and Firmware

Amplification

Tests and Results

Conclusion

Future Work

References

Annexes

1. Introduction

Musicians increasingly rely on compact digital processors capable of real-time effects, amplifier modeling, IR simulation, and wireless control.

This project develops an IoT-enabled digital audio processor, combining:

analog guitar preamp

high-resolution I²S ADC/DAC

real-time DSP

IR convolution

SD-card storage

7 W amplifier

IoT/mobile app support

2. Literature Review

Key areas studied:

DSP and digital audio (Smith, Oppenheim, Zölzer)

Guitar amplifier modeling and IR convolution

Embedded DSP in microcontrollers

I²S digital audio protocol

IoT-enabled audio devices

3. Theoretical Foundation
3.1 Analog Audio and ADC

Guitar signals are low-level, high-impedance ⇒ require:

TL072 preamp

Buffering

Gain control

Soft-clipping

External ADC (PCM1802) for high SNR

3.2 I²S Communication

Used because it provides:

16–32 bit audio

Low latency

Synchronized bit clocks

3.3 DSP Algorithms

Implemented processors include:

Waveshaping distortion

3-band EQ (Biquad filters)

Delay

Reverb

IR convolution (FFT-based)

3.4 Impulse Responses (IRs)

IRs replicate guitar cabinet acoustics using convolution.

4. Methodology

Project followed Scrum — 16 sprints:

Sprints	Focus
1–3	Research & feasibility
4–7	Hardware prototypes
8–12	DSP firmware
13–15	Tests & validation
16	IR loader + amplifier integration
5. System Architecture
5.1 High-Level Architecture Diagram

5.2 Audio Flow
Guitar Input  
    → TL072 Analog Preamp  
        → PCM1802 ADC  
            → ESP32 DSP  
                → PCM5102 DAC  
                    → 7 W Amplifier  
                        → Speaker / Headphones

6. Hardware Design
6.1 Components

ESP32-WROOM

PCM1802 (ADC)

PCM5102A (DAC)

TL072 preamp

PAM8403 / TPA3110 7W amplifier

OLED 0.96”

Potentiometers

Footswitch

SD card module

USB-C power

6.2 Signal Path Diagram

6.3 Full Schematic

6.4 Analog Circuit

7. DSP and Firmware
7.1 Processing Pipeline
I2S Input  
  → Normalize  
  → DSP Effects  
  → IR Convolution  
  → Mixer  
  → I2S Output

7.2 I²S Audio Loop Example
i2s_read(I2S_NUM_0, buffer, buffer_len, &bytes_read, portMAX_DELAY);
process_audio(buffer);
i2s_write(I2S_NUM_0, buffer, buffer_len, &bytes_written, portMAX_DELAY);

7.3 Biquad Filter Example
y[n] = a0*x[n] 
     + a1*x[n-1] 
     + a2*x[n-2] 
     - b1*y[n-1] 
     - b2*y[n-2];

8. Amplification Stage

A Class D 7W amplifier was selected due to:

high efficiency (>90%)

low heat

loud enough for practice

compatible with 5V supplies

Supports:

guitar cabinets

powered speakers

headphones (with attenuation)

9. Tests and Results
9.1 Latency
Stage	Time
ADC → DSP → DAC	10–14 ms
Wireless streaming	35 ms avg
9.2 Audio Quality
Metric	Result
ADC/DAC SNR	95+ dB
Noise	Very low (TL072 op-amp)
IR convolution	High realism
9.3 Power Consumption
Mode	Current
Idle	310 mA
DSP + Amp	350–450 mA
10. Conclusion

The final prototype is a fully functional guitar DSP system capable of real-time effects, IR simulation, and IoT control.

Its low cost and open-source design make it a viable educational and experimental platform.

11. Future Work

Mobile app (Android/iOS)

Convolution reverb

Pitch shift/harmonizer

BLE-MIDI

Multitrack SD recording

Rechargeable Li-ion battery

12. References

SMITH, Julius O. Digital Audio Processing. Stanford, 2011.

OPPENHEIM, A.; SCHAFER, R. Discrete-Time Signal Processing. Prentice Hall, 2010.

ESPRESSIF. ESP32 Technical Reference Manual. 2022.

ZÖLZER, Udo. DAFX – Digital Audio Effects. Wiley, 2011.

IEEE Xplore — IoT audio processing papers.

13. Annexes

Includes:

Schematics

Diagrams

Test recordings

Firmware listings

Hardware photos