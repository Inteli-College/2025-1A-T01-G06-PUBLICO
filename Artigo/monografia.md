Dispositivo IoT para Processamento Digital de Áudio com ESP32 (Monograph)
IoT Audio Processing Device Using ESP32

Author: Gabriel Pascoli Terezo
Institution: Inteli — Institute of Technology and Leadership
Advisor: Prof. Rafael Matsuyama
Year: 2025

Abstract

This monograph presents the development of an IoT-based digital audio processing device using the ESP32 microcontroller. The system operates as a compact audio interface capable of capturing musical signals—primarily electric guitars—applying digital effects, simulating amplifiers and speaker cabinets (Impulse Response / IR), and outputting processed audio in real time through a 7 W analog amplifier.

The proposed device integrates dedicated analog circuitry, high-fidelity ADC/DAC using the I²S protocol, embedded DSP implemented in C/C++, IoT connectivity, SD-card storage, and an optional mobile control application.

This work details the electronic design, the signal chain, DSP algorithms, firmware architecture, system integration and practical validation with real instruments.

Keywords: Audio DSP, IoT, ESP32, Guitar Effects, IR Loader, I²S, Embedded Processing.

Table of Contents

Introduction

Literature Review

Theoretical Foundation

Methodology

System Architecture

Hardware Design

Software & DSP Implementation

Amplification and Analog Output

Tests and Results

Conclusion

Future Work

References

Annexes

1. Introduction

Advances in embedded systems have enabled compact devices to perform tasks previously restricted to dedicated computers. In the context of musical applications—especially electric guitar—there is increasing demand for portable digital processors capable of:

real-time effects processing,

amplifier simulation,

cabinet simulation using IRs,

audio recording,

wireless control, and

integration with mobile applications.

The objective of this work is to design a complete IoT-enabled digital audio processor based on the ESP32 platform, incorporating:

analog guitar preamplification,

high-fidelity I²S ADC and DAC,

real-time DSP (EQ, distortion, IR convolution),

SD storage for IR files and presets,

a 7W class D amplifier,

IoT remote control,

user interface via OLED + potentiometers.

2. Literature Review

The literature review included:

Digital audio processing fundamentals (Smith, Oppenheim, Cook).

DSP algorithms for musical effects (Zölzer, DAFX).

I²S-capable microcontrollers (Espressif).

IR convolution techniques for guitar cabinet emulation.

Commercial DSP processors (HX Stomp, Mooer GE series, Zoom G series).

IoT integration applied to audio devices (IEEE IoT research).

3. Theoretical Foundation
3.1 Audio Capture and ADC

Guitar signals are low-level and high-impedance. Therefore, the device requires:

high-impedance buffer stage,

analog gain stage,

soft-clipping protection,

an external ADC (PCM1802) due to poor ESP32 internal ADC quality.

3.2 I²S Digital Audio Protocol

I²S is used for:

low-latency audio transport,

synchronized clocking,

16/24-bit sample transmission.

The ESP32 supports full-duplex I²S, enabling simultaneous ADC input and DAC output.

3.3 Digital Signal Processing (DSP)

Effects implemented:

Overdrive (nonlinear waveshaping)

3-band EQ (biquad filters)

Delay

Early-reflection reverb

IR convolution for cabinet and amplifier modeling

3.4 Impulse Response (IR) Convolution

Real-time convolution is achieved using:

FFT / iFFT

partitioned convolution to reduce latency

optimized buffers to fit ESP32 RAM limits

4. Methodology

The project followed a Scrum-based development cycle, distributed into 16 sprints:

Sprints 1–3: Research, literature review, and feasibility analysis

Sprints 4–7: Hardware prototyping

Sprints 8–12: DSP firmware development

Sprints 13–15: Testing and refinement

Sprint 16: Integration with amplifier and IR loader

5. System Architecture

A high-level overview is shown below:

Signal flow:

Guitar input → analog preamp

PCM1802 ADC → ESP32 (I²S)

DSP: EQ, distortion, IR, mix

PCM5102A DAC

7W amplifier → speaker/headphones

6. Hardware Design

The device consists of:

ESP32-WROOM

ADC PCM1802

DAC PCM5102A

7W Class-D Amplifier (PAM8403 or TPA3110)

TL072 Preamp

OLED Display (I²C)

Potentiometers for tone/volume/effect control

Footswitch for bypass

SD Card Storage

USB-C Power

6.1 Signal Path Diagram

6.2 Complete Schematic

6.3 Analog Circuit

7. Software & DSP Implementation
7.1 Processing Pipeline

I²S audio input

Normalization

DSP effects

Partitioned IR convolution

Output mixer

I²S DAC output

7.2 I²S Read/Write Example

i2s_read(I2S_NUM_0, buffer, buffer_len, &bytes_read, portMAX_DELAY);
process_audio(buffer);
i2s_write(I2S_NUM_0, buffer, buffer_len, &bytes_written, portMAX_DELAY);

y[n] = a0*x[n] + a1*x[n-1] + a2*x[n-2]
      - b1*y[n-1] - b2*y[n-2];
8. Amplification and Analog Output

A 7W Class D amplifier was chosen because:

High efficiency (>90%)

Clean operation at 5V

Low heat dissipation

Sufficient output volume for practice and monitoring

Compatible with DAC output levels

Supports:

Guitar cabinets

Powered speakers

Headphones (with attenuation)

9. Tests and Results
9.1 Latency

End-to-end latency (ADC → DSP → DAC): 10–14 ms
Acceptable for real-time guitar performance.

9.2 Audio Quality

ADC/DAC SNR: >95 dB

Low noise floor using TL072

IR convolution significantly improved realism

9.3 Power Consumption

350–450 mA under full load

10. Conclusion

The system successfully functions as a portable guitar DSP processor using the ESP32, achieving real-time performance with high-quality effects and cabinet simulation. The combination of analog and digital components produced a reliable, low-cost, open-source alternative to commercial devices.

11. Future Work

Full-featured mobile app

Advanced convolution reverbs

Pitch shifting / harmonizers

BLE-MIDI integration

Multitrack SD recording

Internal rechargeable battery

12. References

SMITH, Julius O. Digital Audio Processing. Stanford, 2011.
OPPENHEIM, A.; SCHAFER, R. Discrete-Time Signal Processing. Prentice Hall, 2010.
ESPRESSIF. ESP32 Technical Reference Manual. 2022.
ZÖLZER, Udo. DAFX – Digital Audio Effects. Wiley, 2011.
IEEE Xplore – IoT audio processing publications.

13. Annexes

This section includes:

All schematics

PCB drafts

Test logs

Audio samples

Additional circuit diagrams