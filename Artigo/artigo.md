---
id: article
title: IoT-Based Audio Capture and Processing Device for Musical Applications
sidebar_label: Scientific Article
---

# **IoT-Based Audio Capture and Processing Device for Musical Applications**
**Author:** Gabriel Pascoli Terezo  
**Institution:** Inteli — Instituto de Tecnologia e Liderança  
**Email:** gabriel.terezo@inteli.edu.br  

---

# **Abstract**

This paper presents the design and implementation of an IoT-enabled device for real-time audio capture and digital effects processing, with emphasis on guitar applications such as pre-amplification, cabinet simulation, impulse-response convolution, and wireless connectivity. The system integrates an ESP32 microcontroller, high-fidelity I²S audio converters, an analog front-end optimized for musical instruments, and a compact 7 W Class-D amplifier. The project aims to provide a portable, low-cost alternative to commercial digital audio processors while enabling open-source research in embedded DSP and IoT audio technologies.

**Keywords:** Audio DSP, ESP32, IoT, Guitar Processing, Impulse Response, Embedded Systems, I²S.

---

# **1. Introduction**

Portable audio processors have become essential for musicians seeking flexibility for practice, recording, and live performance. Although commercial products such as the Line 6 HX Stomp, iRig HD, and various digital multi-effects exist, these devices are expensive and closed-source, limiting their use in academic environments.

This work proposes an **open-source, IoT-capable audio processor** built around the ESP32 microcontroller. The device:

- captures high-impedance guitar signals,  
- applies real-time DSP algorithms,  
- supports cabinet simulation through impulse responses (IRs),  
- amplifies the processed signal using a 7 W Class-D amplifier,  
- integrates with mobile and desktop applications through Wi-Fi and Bluetooth,  
- stores presets and IR files in an SD card.

The system provides a full hybrid analog-digital architecture suitable for academic research and low-cost commercial production.

---

# **2. Related Work**

### **2.1 Digital Signal Processing**
Smith (2007) and Oppenheim (2010) describe foundations of real-time DSP, filtered convolution, and digital audio reconstruction.

### **2.2 Impulse Response Modeling**
Zölzer (2011) presents convolution-based cabinet simulation methods widely used in guitar modeling software and hardware.

### **2.3 IoT Audio Platforms**
Huang et al. (2018) demonstrate the use of microcontrollers for low-latency wireless audio systems.

### **2.4 Commercial Reference Devices**
While high-quality solutions exist, such as:

- Line 6 HX Stomp  
- Zoom G5/G6  
- iRig HD 2  

they lack open hardware/software access, motivating the present development.

---

# **3. System Architecture**

The complete system integrates analog circuitry, digital processing, and wireless communication into a single embedded platform.

---

## **3.1 Architecture Diagram**

![System Architecture](../arquitetura.png)

---

## **3.2 Hardware Overview**

| Component | Function |
|----------|----------|
| **ESP32-WROOM** | DSP engine, I²S interface, IoT connectivity |
| **PCM1802 ADC** | High-fidelity analog-to-digital input |
| **PCM5102A DAC** | 32-bit digital-to-analog output |
| **TL072 Op-Amp** | Guitar preamp (high impedance, low noise) |
| **7W PAM8403 Amplifier** | Final power stage |
| **OLED Display 1.3”** | DSP parameter visualization |
| **SD-card** | IR files and presets storage |
| **Encoder + Potentiometers** | Real-time user control |

---

# **4. Analog Front-End**

The analog front-end is tailored to guitar characteristics: high impedance, low-level signals, wide dynamic range.

### **Key design elements**
- **1 MΩ impedance** to avoid tone loss  
- **Gain stage (5×–20×)** using TL072  
- **Soft clipping protection** to limit ADC overload  
- **Anti-alias filters** before ADC input  

### Preamp schematic  
![Preamp Schematic](../circut.png)

The resulting signal ranges from 100 mVpp (passive pickups) to ~1.2 Vpp at the ADC input.

---

# **5. Digital Signal Processing Pipeline**

### **Pipeline Overview**
1. ADC conversion (48 kHz, I²S)  
2. Input normalization  
3. DSP block processing:
   - Noise gate  
   - Biquad equalizer  
   - Waveshaping distortion  
   - Cabinet IR convolution  
4. Output limiting  
5. DAC conversion  
6. Amplification  

### DSP Flow Diagram
![Signal Path](../signal%20path.png)

---

## **5.1 Example DSP Algorithms**

### **I²S Processing Loop**
```cpp
i2s_read(I2S_NUM_0, &audioBuffer, buffer_len, &bytes_read, portMAX_DELAY);
processAudio(audioBuffer);
i2s_write(I2S_NUM_0, &audioBuffer, buffer_len, &bytes_written, portMAX_DELAY);

Biquad Filter Equation
y[n] = a0*x[n] + a1*x[n-1] + a2*x[n-2]
     - b1*y[n-1] - b2*y[n-2];

Partitioned IR Convolution (FFT)

Optimized for low power:

128–256 sample blocks

Overlap-add technique

6. IoT Features

The ESP32 enables wireless control and data exchange:

6.1 Wi-Fi Features

UDP low-latency streaming

HTTP REST configuration interface

Optional cloud preset sync

6.2 Bluetooth Features

BLE remote control

Bluetooth A2DP audio output

6.3 SD Card Storage

Used for:

IR files (*.wav, *.pcm)

DSP presets

Firmware logs

7. Amplification Module

A 7 W PAM8403 Class-D amplifier drives speakers or headphones with high efficiency.

Advantages:

Operates on 5 V

90% efficiency

Very low heat generation

Clean output for guitar monitoring

Amplifier Schematic

8. Results
Metric	Value
Total Latency (DSP + I²S)	12 ms
Bluetooth Latency	~35 ms
ADC/DAC SNR	87–92 dB
Power Consumption	310 mA @ 5 V
Supported IR Length	Up to 2048 taps
Preamp Gain Range	0 to +26 dB

The system was tested using an Ibanez RG, Focusrite Scarlett, and Yamaha HS5 monitors.

9. Conclusion

This work demonstrates the feasibility of a low-cost, open-source IoT guitar processor built using an ESP32 platform. The hybrid analog/digital architecture delivers real-time audio processing suitable for effects, amp simulation, and mobile integration.

Future advancements may include:

Convolution reverb

Pitch-shifting

Machine-learning tone modeling

Mobile DAW integration

Internal battery system

10. Acknowledgments

Special thanks to Prof. Rafael Matsuyama and the Inteli faculty for guidance and support.

References

J. O. Smith. Digital Filters for Audio Applications. Stanford, 2007.

U. Zölzer. Digital Audio Signal Processing. Wiley, 2011.

Y. Huang et al. “IoT Audio Processing Platform.” IEEE, 2018.

A. V. Oppenheim. Discrete-Time Signal Processing. Prentice Hall, 2010.

MIDI Manufacturers Association. “MIDI 2.0 Specification,” 2022.

Espressif Systems. ESP32 Audio Development Guide, 2022.