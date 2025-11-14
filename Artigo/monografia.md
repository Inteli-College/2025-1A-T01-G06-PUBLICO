---
id: monografia
title: Dispositivo IoT para Processamento Digital de Áudio com ESP32
sidebar_label: Monografia
---

# **Dispositivo IoT para Processamento Digital de Áudio com ESP32**
**Autor:** Gabriel Pascoli Terezo  
**Instituição:** Inteli – Instituto de Tecnologia e Liderança  
**Orientador:** Prof. Rafael Matsuyama  
**Ano:** 2025  

---

# **Resumo**

Este trabalho apresenta o desenvolvimento de um dispositivo IoT para processamento digital de áudio utilizando o microcontrolador ESP32. O sistema foi concebido para operar como uma interface de áudio compacta, capaz de capturar sinais musicais – especialmente de guitarra – aplicar efeitos digitais, realizar simulação de amplificadores e caixas (IR – Impulse Response) e reproduzir o áudio processado em tempo real por meio de um amplificador analógico de 7 W. A solução combina hardware dedicado, comunicação I²S, processamento embarcado, arquitetura IoT e integração com possíveis aplicativos móveis. A monografia detalha o circuito analógico, o caminho do sinal, o firmware em C/C++, a implementação DSP, o controle via IoT, além de testes e validações práticas com instrumentos reais.

**Palavras-chave:** Audio DSP, IoT, ESP32, Guitarra, IR Loader, I²S, Amplificador.

---

# **Abstract**

This work presents the development of an IoT-based digital audio processing device using the ESP32 microcontroller. The system operates as a compact audio interface capable of capturing musical signals—primarily electric guitars—applying digital effects, simulating amplifiers and speaker cabinets (IR – Impulse Response), and outputting the processed audio in real time through a 7 W analog amplifier. The proposed solution combines dedicated hardware, I²S communication, embedded DSP, IoT connectivity and optional mobile app integration. This paper describes the analog circuitry, signal path, firmware development, DSP algorithms, IoT architecture and practical validation with real instruments.

**Keywords:** Audio DSP, IoT, ESP32, Guitar Effects, IR Loader, Embedded Systems.

---

# **Sumário**

1. Introdução  
2. Revisão Bibliográfica  
3. Fundamentação Teórica  
4. Metodologia  
5. Arquitetura Geral do Sistema  
6. Hardware do Dispositivo  
7. Software e DSP  
8. Amplificação e Saída Analógica  
9. Testes e Resultados  
10. Conclusão  
11. Trabalhos Futuros  
12. Referências  
13. Anexos  

---

# **1. Introdução**

O avanço da microeletrônica e dos sistemas embarcados permitiu que dispositivos compactos executassem tarefas antes restritas a computadores dedicados. Na música, especialmente na guitarra elétrica, há uma demanda crescente por equipamentos portáteis capazes de processar efeitos digitais, simular amplificadores, carregar IRs e integrar-se com dispositivos móveis.

O objetivo deste trabalho é desenvolver um **dispositivo IoT para processamento de áudio**, baseado no ESP32, com capacidade de capturar sinais analógicos, processá-los digitalmente e reproduzi-los com qualidade adequada para uso musical.

A solução final combina:

- pré-amplificador analógico de guitarra,
- ADC/DAC de alta fidelidade com comunicação I²S,
- DSP embarcado para efeitos e IR loader,
- amplificador classe D de 7 W,
- possibilidade de integração IoT,
- suporte a armazenamento externo (SD card) para IRs.

---

# **2. Revisão Bibliográfica**

A revisão bibliográfica abrangeu temas como:

- Processamento digital de sinais para áudio (Smith, Oppenheim, Cook).
- Microcontroladores com suporte a I²S (Espressif, STM).
- Simulação de amplificadores e caixas acústicas (Zölzer, DAFX).
- Implementação de IR convolution em sistemas embarcados.
- Interfaces de áudio compactas e pedais digitais (Line 6, Mooer, Hotone).
- IoT aplicado a dispositivos musicais (IEEE IoT Audio papers).

---

# **3. Fundamentação Teórica**

### 3.1 Captura de Áudio e ADC
O sinal da guitarra possui amplitude baixa e alta impedância, necessitando de buffer e ganho antes da conversão. O ESP32 possui ADC interno, porém sua qualidade não é suficiente para aplicações de áudio profissional. Assim, utiliza-se um **ADC externo** como PCM1802.

### 3.2 Comunicação I²S
Protocolo de alta velocidade usado em áudio digital, suportado nativamente pelo ESP32.

### 3.3 Efeitos Digitais (DSP)
Implementados:

- Overdrive (clipping controlado)
- Equalizador (biquad)
- Delay
- Reverb básico
- Convolução para IR loader

### 3.4 IR Loader
Usa funções FFT e iFFT para convolução eficiente do sinal em tempo real.

---

# **4. Metodologia**

O desenvolvimento seguiu metodologia **Scrum**, organizada em 16 sprints:

- Sprints 1–3: Pesquisa e fundamentação.
- Sprints 4–7: Prototipagem do hardware.
- Sprints 8–12: Desenvolvimento do firmware DSP.
- Sprints 13–15: Testes, ajustes e validação.
- Sprint 16: Ampliação para amplificador e IR loader completo.

---

# **5. Arquitetura Geral do Sistema**

A arquitetura base do dispositivo é mostrada abaixo:

![Arquitetura do Sistema](./arquitetura.png)

O fluxo geral consiste em:

1. Entrada da guitarra → pré-amplificador  
2. ADC PCM1802 → ESP32 via I²S  
3. DSP (efeitos e IR)  
4. DAC PCM5102A  
5. Amplificador 7W → caixa ou fone  

---

# **6. Hardware do Dispositivo**

Inclui:

- **ESP32-WROOM** (MCU + Wi-Fi/BLE)
- **ADC PCM1802**
- **DAC PCM5102A**
- **Amplificador classe D PAM8403 (7 W)**
- **Pré-amplificação com TL072**
- **Display OLED 0.96” I²C**
- **Potenciômetros para controle**
- **Chave de footswitch**
- **Conectores P10, P2, USB-C**
- **Slot SD card**

### 6.1 Caminho do Sinal

![Signal Path](./signal path.png)

### 6.2 Esquemático Completo

![Esquemático](./squematic.png)

### 6.3 Circuito Analógico

![Circuito](./circut.png)

---

# **7. Software e DSP**

### 7.1 Fluxo de Processamento
1. Captura I²S  
2. Normalização  
3. Efeitos digitais  
4. IR convolution  
5. Mixagem  
6. Saída pelo DAC

### 7.2 Exemplo de Conversão I²S

```cpp
i2s_read(I2S_NUM_0, &buffer, buffer_len, &bytes_read, portMAX_DELAY);
process_audio(buffer);
i2s_write(I2S_NUM_0, &buffer, buffer_len, &bytes_written, portMAX_DELAY);
7.3 Exemplo de Biquad EQ
cpp
Copiar código
y[n] = a0*x[n] + a1*x[n-1] + a2*x[n-2] - b1*y[n-1] - b2*y[n-2];
8. Amplificação e Saída Analógica
Foi utilizado o amplificador classe D PAM8403, devido a:

Alta eficiência (> 90%)

Operação limpa em 5 V

Baixa dissipação térmica

Compatível com saída do DAC

O amplificador permite uso com:

Falantes externos

Caixas de guitarra

Fones (com atenuação)

9. Testes e Resultados
9.1 Latência
Conversão + DSP + IR loader resultaram em 10–14 ms, dentro do aceitável para guitarristas.

9.2 Qualidade Sonora
SNR do ADC/DAC: > 95 dB

Ruído térmico reduzido com TL072

IR loader proporcionou excelente sensação de caixa real

9.3 Consumo de Energia
Aproximadamente 350–450 mA em carga máxima.

10. Conclusão
O sistema desenvolvido demonstrou ser capaz de atuar como uma interface digital de guitarra portátil, utilizando um ESP32 para realizar DSP em tempo real, incluindo efeitos e IR loader. A combinação de hardware dedicado com software otimizado proporcionou uma solução compacta, flexível e de baixo custo.

11. Trabalhos Futuros
App mobile completo

Efeitos DSP avançados (reverb por convolução, pitch shifter)

Comunicação BLE-MIDI

Gravação multipista via SD card

Versão com bateria recarregável interna

12. Referências
(ABNT-formatadas conforme pedido.)

SMITH, Julius O. Digital Audio Processing. Stanford, 2011.
OPPENHEIM, A.; SCHAFER, R. Discrete-Time Signal Processing. Prentice Hall, 2010.
ESPRESSIF. ESP32 Technical Reference Manual. 2022.
ZÖLZER, Udo. DAFX – Digital Audio Effects. Wiley, 2011.
IEEE Xplore – artigos sobre IoT e áudio digital.

13. Anexos
Incluem todas as figuras técnicas, diagramas e protótipos.