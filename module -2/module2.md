
# 📚 Module 2 — Full Sprint Summary and Documentation

This module presents a summarized overview of all 10 sprints that led to the development of the **IoT Audio and MIDI Controller** device. Each sprint progressively contributed to hardware design, software implementation, integration, and testing.

---

## 🧾 Project Overview

The project goal was to create a compact, portable device capable of:
- Capturing high-quality audio using ADC/DAC systems.
- Sending MIDI commands through physical push-buttons.
- Routing analog audio signals through XLR/TRS connectors.
- Supporting connectivity with computers via USB and mobile via wireless interfaces.

---

## 🗓️ Sprint-by-Sprint Summary

### 🟢 Sprint 1 — Research and Requirements
- Defined product scope and target user (musicians, producers).
- Researched MIDI protocol, audio interfaces, and IoT integration.
- Defined minimum viable product (MVP) features.

### 🟢 Sprint 2 — Component Study and Circuit Prototyping
- Evaluated electronic components: microcontrollers, op-amps, combo jacks.
- Created initial breadboard prototype for MIDI switching.
- Validated push-button responsiveness.

### 🟢 Sprint 3 — Audio Signal Path Testing
- Designed simple analog audio passthrough using XLR and TRS.
- Tested noise levels and signal integrity.
- Simulated input/output impedance matching.

### 🟢 Sprint 4 — Embedded Software Setup
- Set up embedded development environment (Arduino IDE with MIDIUSB).
- Sent first MIDI Note On/Off messages.
- Created basic loop for 4 switches.

### 🟢 Sprint 5 — Firmware Expansion & IR Planning
- Expanded firmware to handle 8 switches.
- Studied IR file loading architecture for future plugin simulation.
- Defined file handling structure (for SD card support).

### 🟢 Sprint 6 — Prototyping Enclosure & PCB Draft
- Created first PCB schematic using KiCad/Fritzing.
- Designed 3D printable case prototype.
- Aligned physical layout of jacks and buttons.

### 🟢 Sprint 7 — MIDI USB + DIN Integration
- Enabled USB MIDI device functionality (Class Compliant).
- Added MIDI IN and OUT using 5-pin DIN ports.
- Implemented channel selection logic in firmware.

### 🟢 Sprint 8 — Circuit Finalization + Docs
- Created schematic for full system (MIDI + Audio).
- Connected 8 switches, combo jacks, microcontroller in final circuit.
- Wrote technical documentation and generated Docusaurus pages.

### 🟢 Sprint 9 — User Feedback + Testing
- Collected feedback from musicians (latency, feel, reliability).
- Adjusted switch debounce delay.
- Validated MIDI compatibility with DAWs and hardware synths.

### 🟢 Sprint 10 — Final Assembly and Polish
- Integrated all hardware into final enclosure.
- Optimized software and tested for stability.
- Prepared for project presentation and demonstration.

---

## 📁 Directory Summary

```
/docs/
├── intro.md            ← Project overview
├── sprint1-10.md       ← Individual sprint docs
├── module2.md          ← This summary file
/images/
├── assembled_device.jpg
├── midi_controller_circuit.png
/hardware/
├── pcb_layout.sch
├── enclosure_model.stl
/firmware/
├── midi_controller.ino
```

---

## 🎯 Key Accomplishments

- ✅ Fully functional 8-button MIDI controller
- ✅ USB and DIN MIDI support
- ✅ Audio passthrough using professional combo jacks
- ✅ Modular firmware for custom note/channel assignment
- ✅ Clean and accessible documentation in Markdown and Docusaurus
- ✅ Community collaboration readiness

---

## 📌 Next Steps (Beyond Module 2)

- Add real-time IR plugin handling for cabinet simulation
- Support expression pedals or faders for MIDI CC
- Integrate Bluetooth LE MIDI for wireless control
- Design a polished PCB for manufacturing

---

**Module Completed by:** Gabriel Pascoli  
**Institution:** Inteli  
**Delivery Date:** June 30, 2025
