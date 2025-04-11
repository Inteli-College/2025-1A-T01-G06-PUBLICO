# 🎧 Module 1 – Research and Hardware Prototyping for Audio with IoT

This repository gathers the studies, tests, and technical decisions made during the first phase of the project. The central goal of this module was to investigate viable solutions for a portable digital audio device, with IoT capabilities and integration between analog circuits and digital processing.

## 🚀 Module Focus
Create the technical foundation of the project:

- Research technologies and protocols related to digital audio.
- Select and test key electronic components.
- Build a first functional and integrated prototype.

## 🏆 Stage Highlights
- Bibliographic survey focusing on analog audio circuits, ADC/DAC, and digital communication.
- Component selection based on cost-benefit and performance.
- Assembly and testing of the analog circuit with gain adjustments and filtering.
- Development of basic firmware for audio capture and transmission.
- First tests with MIDI and communication with DAWs and mobile devices.

## 📚 References
- Smith, J. O. – Digital Filters with Audio Applications, Stanford (2007).
- Zölzer, U. – Digital Audio Signal Processing, Wiley (2011).
- Huang, Y. et al. – IoT Audio Processing Platform, IEEE (2018).
- Arduino Docs – Audio input techniques.
- STMicroelectronics – STM32 ADCs for analog signals.
- TI – Operational amplifiers for audio.
- Maxim – Analog front-end design.
- Espressif – Audio with ESP32.
- IEEE – Audio transmission via Wi-Fi.
- MIDI 2.0 – Specifications from the Open Music Initiative.

## 🔧 Key Components Used
- ESP32-WROOM (MCU)
- PCM1802 (ADC) and PCM5102A (DAC)
- TL072, NE5532 (Op-Amps)
- Passive filters, voltage regulators
- P10, P2, MIDI connectors
- UART, I²S, Bluetooth interfaces

## 📁 Project Organization
- `sprint-1/`: Initial plan and schedule
- `sprint-2/`: Technical survey and component selection
- `sprint-3/`: Circuit assembly and audio testing
- `sprint-4/`: Firmware and basic integration
- `sprint-5/`: Consolidated prototype and validation tests

## ✅ Module Conclusion
The first module has been successfully completed. With the prototype up and running and the technologies tested in the field, we now have a solid foundation to evolve the project: create the graphical interface, import IR plugins, customize presets, and expand usage possibilities for live performances and studio environments.
