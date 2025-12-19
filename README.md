🎸 IoT Guitar FX – ESP32 + DSP + 7W Amplifier
Sistema IoT para Processamento Digital de Áudio com ESP32
IoT Audio Processing System for Guitar Effects using ESP32
🌎 Languages / Idiomas

🇧🇷 Leia em Português

🇺🇸 Read in English

🇧🇷 VERSÃO EM PORTUGUÊS
🎸 IoT Guitar FX – ESP32 + DSP + Amplificador 7W

Este projeto apresenta um dispositivo IoT para processamento digital de efeitos de guitarra, combinando hardware analógico, DSP em tempo real, interface I²S, IRs, conectividade e amplificador integrado.

📽 Apresentação Oficial

🔗 Canva Presentation:
https://www.canva.com/design/DAG4sYYO-wU/y5F-14GGp2GgDcIg7vRv0g/edit

📚 Documentação Completa
📘 Monografia (ABNT 2023)

👉 Abrir monografia

📄 Artigo Científico (IEEE)

👉 Abrir artigo

🖼 Diagramas e Esquemáticos
Arquivo	Descrição
arquitetura.png
	Arquitetura geral do sistema
signal path.png
	Pipeline DSP
squematic.png
	Esquemático eletrônico
circut.png
	Circuito do amplificador 7W
💰 Tabela de Preços dos Componentes (Estimativa)
Componente	Quantidade	Preço (R$)	Total
ESP32 WROOM	1	R$ 35,00	R$ 35,00
ADC PCM1802	1	R$ 45,00	R$ 45,00
DAC PCM5102A	1	R$ 40,00	R$ 40,00
Amplificador 7W (PAM8407/TPA3110)	1	R$ 25,00	R$ 25,00
TL072 (Op-Amp)	1	R$ 7,00	R$ 7,00
OLED 1.3"	1	R$ 28,00	R$ 28,00
Encoder Rotativo	1	R$ 12,00	R$ 12,00
Potenciômetros	3	R$ 5,00	R$ 15,00
Cartão SD + módulo	1	R$ 22,00	R$ 22,00
Placa PCB (10x10 cm)	1	R$ 50,00	R$ 50,00
Conectores P10 / P2	2	R$ 8,00	R$ 16,00
Fonte 5V 2A	1	R$ 30,00	R$ 30,00
Caixa / Case	1	R$ 40,00	R$ 40,00
💵 Custo Total Estimado: R$ 365 – R$ 420
🎯 Objetivos do Projeto

Processar efeitos de guitarra em tempo real

Simular amplificadores/válvulas e gabinetes (IRs)

Oferecer interface IoT (controle por app/PC)

Possibilidade de gravação em SD Card

Saída amplificada para caixas ativas ou fone

🎚 Tecnologias
Hardware

ESP32

I²S ADC/DAC

TL072 preamp

Amplificador Classe D

Display OLED

Software

DSP em C/C++

FFT + Convolução IR

EQ, distorção, modulação

Wi-Fi + Bluetooth

✨ Autoria

Gabriel Pascoli Terezo – Engenharia da Computação
Orientador: Prof. Rafael Matsuyama – INTELI

🇺🇸 ENGLISH VERSION
🎸 IoT Guitar FX – ESP32 + DSP + 7W Amplifier

This project introduces an IoT-enabled guitar effects processor with real-time DSP, analog front-end, IR convolution, I²S audio pipeline, SD storage, and integrated power amplifier.

📽 Presentation

🔗 Official Canva Presentation:
https://www.canva.com/design/DAG4sYYO-wU/y5F-14GGp2GgDcIg7vRv0g/edit

📚 Documentation
📘 Thesis (ABNT 2023 in PT-BR)

👉 Open monograph

📄 Scientific Article (IEEE)

👉 Open article

🖼 System Diagrams
File	Description
arquitetura.png
	Full architecture
signal path.png
	DSP pipeline
squematic.png
	Electronic schematic
circut.png
	Power amplifier
💰 Component Price Table (USD Approx.)
Component	Qty	Price (USD)	Total
ESP32 WROOM	1	$7	$7
ADC PCM1802	1	$9	$9
DAC PCM5102A	1	$8	$8
7W Amplifier (PAM8407/TPA3110)	1	$5	$5
TL072 Op-Amp	1	$2	$2
OLED 1.3"	1	$6	$6
Rotary Encoder	1	$3	$3
Potentiometers	3	$1	$3
SD Card Module	1	$5	$5
PCB (10×10 cm)	1	$15	$15
Audio Connectors	2	$2	$4
Power Supply 5V	1	$6	$6
Enclosure	1	$12	$12
Total Estimated Cost: $85 – $95
🎯 Project Goals

Real-time DSP guitar effects

Cabinet/amp IR simulation

IoT remote control (WebApp/PC/phone)

SD Card recording & IR storage

Built-in audio amplification

🧠 Technologies
Hardware

ESP32

I²S audio codec

TL072 preamp

Class D amplifier

OLED display

Software

DSP in C/C++

FFT + Partitioned Convolution

EQ, distortion, modulation

Wi-Fi / Bluetooth

✨ Author

Gabriel Pascoli Terezo – Computer Engineering
Advisor: Prof. Rafael Matsuyama – INTELI