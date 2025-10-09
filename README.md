# 🎧 IoT Audio Device – Smart Audio Interface for Musicians  
![Pac-Man Animation](https://media.giphy.com/media/e0Z3sMVF0DewU/giphy.gif)

> 🎶 *Connecting analog warmth to digital intelligence through IoT and embedded systems.*

---

## 📘 About This Project  

This repository documents the **entire development of an IoT-based Audio Device**, designed to combine **analog audio processing** with **digital automation and connectivity**.  
The device aims to provide musicians and producers with a **portable, high-fidelity** solution for capturing, converting, and transmitting audio through **Bluetooth, Wi-Fi, and USB interfaces**.  

---

## 🚀 Project Overview  

### 🎯 Core Objective  
Develop a hybrid audio interface capable of:
- Converting analog signals to digital in real-time.  
- Supporting connections such as MIDI, P10, and P2.  
- Communicating with computers and mobile devices.  
- Allowing audio customization via a DAW-style mobile interface.  

---

## 🧭 Methodology  

The project followed an **Agile (Scrum)** approach across **15 sprints**, progressively refining both hardware and software.  
Each sprint involved literature review, prototyping, firmware testing, and real-world validation with musical instruments.

### 📅 Development Timeline (15 Sprints)

| Sprint | Focus | Highlights |
|:------:|:------|:------------|
| 1–2 | Research & Planning | Bibliographic review, hardware selection |
| 3–5 | Prototyping | Analog circuit construction, signal testing |
| 6–8 | Integration | Firmware + connectivity (MIDI, Wi-Fi, Bluetooth) |
| 9–11 | Optimization | Power efficiency, latency testing |
| 12–13 | Documentation | Final test reports and academic writing |
| 14–15 | Finalization | Complete prototype, live demos, and presentation |

---

## 🔧 Core Components  

| Category | Component | Function |
|-----------|------------|-----------|
| **MCU** | ESP32-WROOM | Core microcontroller with Wi-Fi/Bluetooth |
| **ADC/DAC** | PCM1802 / PCM5102A | High-fidelity audio conversion |
| **Op-Amps** | TL072 / NE5532 | Analog signal conditioning |
| **Connectivity** | MIDI DIN, P10, P2, USB-C | Multiple I/O formats |
| **Power** | Li-Ion Battery + Regulator | Portable operation |
| **Interface** | I²S / UART / BLE | Communication channels |

---

## 🧠 Technical Highlights  

- Audio fidelity above **90 dB SNR**  
- Latency below **10 ms (wired)** and **25 ms (wireless)**  
- Support for **IR plugins** and **customizable presets**  
- Tested with **guitars, keyboards, and microphones**  
- Compatible with **desktop DAWs and mobile apps**  

---

## 🧩 Repository Structure  

# 🎧 IoT Audio Device – Smart Audio Interface for Musicians  
![Pac-Man Animation](https://media.giphy.com/media/e0Z3sMVF0DewU/giphy.gif)

> 🎶 *Connecting analog warmth to digital intelligence through IoT and embedded systems.*

---

## 📘 About This Project  

This repository documents the **entire development of an IoT-based Audio Device**, designed to combine **analog audio processing** with **digital automation and connectivity**.  
The device aims to provide musicians and producers with a **portable, high-fidelity** solution for capturing, converting, and transmitting audio through **Bluetooth, Wi-Fi, and USB interfaces**.  

---

## 🚀 Project Overview  

### 🎯 Core Objective  
Develop a hybrid audio interface capable of:
- Converting analog signals to digital in real-time.  
- Supporting connections such as MIDI, P10, and P2.  
- Communicating with computers and mobile devices.  
- Allowing audio customization via a DAW-style mobile interface.  

---

## 🧭 Methodology  

The project followed an **Agile (Scrum)** approach across **15 sprints**, progressively refining both hardware and software.  
Each sprint involved literature review, prototyping, firmware testing, and real-world validation with musical instruments.

### 📅 Development Timeline (15 Sprints)

| Sprint | Focus | Highlights |
|:------:|:------|:------------|
| 1–2 | Research & Planning | Bibliographic review, hardware selection |
| 3–5 | Prototyping | Analog circuit construction, signal testing |
| 6–8 | Integration | Firmware + connectivity (MIDI, Wi-Fi, Bluetooth) |
| 9–11 | Optimization | Power efficiency, latency testing |
| 12–13 | Documentation | Final test reports and academic writing |
| 14–15 | Finalization | Complete prototype, live demos, and presentation |

---

## 🔧 Core Components  

| Category | Component | Function |
|-----------|------------|-----------|
| **MCU** | ESP32-WROOM | Core microcontroller with Wi-Fi/Bluetooth |
| **ADC/DAC** | PCM1802 / PCM5102A | High-fidelity audio conversion |
| **Op-Amps** | TL072 / NE5532 | Analog signal conditioning |
| **Connectivity** | MIDI DIN, P10, P2, USB-C | Multiple I/O formats |
| **Power** | Li-Ion Battery + Regulator | Portable operation |
| **Interface** | I²S / UART / BLE | Communication channels |

---

## 🧠 Technical Highlights  

- Audio fidelity above **90 dB SNR**  
- Latency below **10 ms (wired)** and **25 ms (wireless)**  
- Support for **IR plugins** and **customizable presets**  
- Tested with **guitars, keyboards, and microphones**  
- Compatible with **desktop DAWs and mobile apps**  

---

## 🧩 Repository Structure  

┣ 📁 sprint-1/ → Initial planning and project schedule
┣ 📁 sprint-2/ → Bibliographic review and component selection
┣ 📁 sprint-3/ → Circuit prototyping and analog testing
┣ 📁 sprint-4/ → Firmware and digital signal integration
┣ 📁 sprint-5/ → User interface and connectivity tests
┣ 📁 sprint-6–15/ → Refinement, documentation, final prototype
┣ 📜 README.md → Main project summary (this file)
┗ 📄 TCC.md → Full academic documentation (UNICAMP/ABNT style)


---

## 🧾 Academic Summary  

This work was developed as part of the **Final Graduation Project** for the **Computer Engineering program at Inteli (Instituto de Tecnologia e Liderança)**.  
It aims to bridge the gap between **hardware engineering** and **music production**, leveraging IoT to create an intelligent, musician-friendly tool.  

---

## 📚 References  

1. Smith, J. O. – *Digital Filters with Audio Applications.* Stanford, 2007.  
2. Zölzer, U. – *Digital Audio Signal Processing.* Wiley, 2011.  
3. Huang, Y. et al. – *IoT Audio Processing Platform.* IEEE, 2018.  
4. Oppenheim, A. V. – *Discrete-Time Signal Processing.* Prentice Hall, 2010.  
5. Dellinger, J. – *High-Fidelity Audio Engineering for IoT Devices.* IEEE, 2020.  
6. Espressif Systems – *ESP32 Audio Development Guide.* 2022.  
7. TI & Maxim Integrated – *Audio Front-End Design Notes.*  
8. Open Music Initiative – *MIDI 2.0 Specification.*  
9. Arduino & STMicroelectronics Docs – *ADC Techniques for Audio Capture.*  
10. IEEE Xplore – *Low-Latency Audio Transmission in IoT Devices.*  

---

## 🧠 Future Work  

- Expand plugin integration (VST/IR) for advanced audio modeling.  
- Implement real-time DSP effects within the firmware.  
- Enhance DAW-style mobile interface for editing and mixing.  
- Research adaptive noise suppression using AI audio filters.  

---

## 🎓 Acknowledgments  

Special thanks to **Prof. Daniela** for her guidance, to **Inteli** for academic support, and to all collaborators who contributed to this project.  
And, of course, to the musicians who inspired the technical pursuit of sound perfection 🎸🎚️  

---

> **“Where engineering meets creativity — every signal matters.”**  

![Pac-Man Animation](https://media.giphy.com/media/3oEjHI8mUue5a5FuNO/giphy.gif)
