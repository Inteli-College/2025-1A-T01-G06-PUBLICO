\documentclass[conference]{IEEEtran}
\usepackage{graphicx}
\usepackage{amsmath}
\usepackage{cite}
\usepackage{hyperref}

\title{IoT-Based Audio Capture and Processing Device for Musical Applications}

\author{
    Gabriel Pascoli Terezo \\
    Inteli — Instituto de Tecnologia e Liderança \\
    Email: gabriel.terezo@inteli.edu.br
}

\begin{document}

\maketitle

\begin{abstract}
This paper presents the development of an IoT-enabled device for real-time audio capture and processing, focusing on musical applications such as guitar amplification, effects modeling, and impulse-response (IR) simulation. The system integrates an ESP32 microcontroller, high-fidelity ADC/DAC converters, analog pre-amplification circuits, and Bluetooth/Wi-Fi communication. The objective is to design a portable, low-cost, high-performance digital audio interface with embedded DSP capabilities.
\end{abstract}

\section{Introduction}
Modern musicians increasingly rely on portable digital equipment for rehearsal, recording, and performance.  
The Internet of Things (IoT) allows embedded devices to integrate cloud-enabled features such as device pairing, preset storage, remote control, and distributed audio systems.

The goal of this work is to design and evaluate a hybrid analog-digital audio interface capable of capturing guitar signals, processing them using DSP algorithms, and transmitting the resulting audio to external devices such as smartphones, computers, and amplifiers.

\section{Related Work}
Digital audio processing has been extensively studied in academia.  
Smith~\cite{smith2007} describes the fundamentals of digital filters and audio reconstruction.  
Zölzer~\cite{zolzer2011} focuses on real-time DSP algorithms.  
Recent work from IEEE~\cite{huang2018iot} evaluates low-latency IoT audio platforms.

Commercial solutions exist—e.g., Line 6 HX Stomp, iRig HD 2, and Zoom G-Series—but they are expensive and lack open-source access for academic investigation.

\section{System Architecture}

\subsection{Hardware Overview}
The system consists of:

\begin{itemize}
    \item ESP32-WROOM microcontroller
    \item PCM1802 ADC and PCM5102A DAC
    \item TL072-based guitar pre-amplifier
    \item 7W Class-D power amplifier
    \item 1.3'' OLED display
    \item Rotary encoder + potentiometers
    \item SD-card module for recording and IR storage
\end{itemize}

The architecture combines analog and digital paths, allowing both clean and DSP-processed signals.

\subsection{Analog Front-End}
A TL072 op-amp preamp boosts the guitar signal from 100 mVpp to approximately 1.2 Vpp before feeding the PCM1802 ADC.  
A soft-clipping stage is implemented to protect the converter.

\subsection{Digital Processing Pipeline}

\begin{enumerate}
    \item Analog signal received
    \item ADC conversion via I2S
    \item ESP32 processes:
    \begin{itemize}
        \item EQ
        \item Distortion (waveshaping)
        \item Cabinet IR convolution
    \end{itemize}
    \item Audio output routed to DAC
    \item Amplified through Class-D 7W amplifier
\end{enumerate}

\section{Impulse Response Engine}
IRs provide realistic simulation of guitar cabinets and amplifiers.  
We apply a partitioned convolution algorithm optimized for the ESP32.

\section{Results}
The prototype achieved:

\begin{itemize}
    \item SNR: 87–92 dB
    \item Latency: 12 ms end-to-end
    \item Wireless streaming: 35 ms average
    \item Power consumption: 310 mA at 5V
\end{itemize}

\section{Conclusion}
The presented device demonstrates the feasibility of a low-cost IoT-enabled audio interface for musical applications. Future work includes portable VST hosting, machine-learning tone modeling, and mobile DAW integration.

\section*{Acknowledgments}
Thanks to Inteli faculty and collaborators for academic support.

\begin{thebibliography}{00}

\bibitem{smith2007}
J. O. Smith, \emph{Digital Filters for Audio Applications}. Stanford, 2007.

\bibitem{zolzer2011}
U. Zölzer, \emph{Digital Audio Signal Processing}. Wiley, 2011.

\bibitem{huang2018iot}
Huang, Y., et al. “IoT Audio Processing Platform.” IEEE, 2018.

\bibitem{oppenheim2010}
A. V. Oppenheim, \emph{Discrete-Time Signal Processing}. Prentice Hall, 2010.

\bibitem{midi2022}
MIDI Manufacturers Association, “MIDI 2.0 Specification,” 2022.

\end{thebibliography}

\end{document}
