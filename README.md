# Pulse-Code-Modulation

Aim

The aim of this program is to simulate the Pulse Code Modulation (PCM) process, where an analog message signal is converted into a digital signal through sampling and quantization.

Tools required

Python: A versatile programming language used for scientific computing and signal processing. NumPy: A powerful numerical library in Python for performing array-based operations and mathematical computations. Matplotlib: A plotting library for generating high-quality graphs and visualizations of data, essentialfor demonstrating the sampling process.

Program

import matplotlib.pyplot as plt import numpy as np

sampling_rate = 5000 frequency = 50 duration = 0.1 quantization_levels = 16

t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

message_signal = np.sin(2 * np.pi * frequency * t)

clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))

quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels quantized_signal = np.round(message_signal / quantization_step) * quantization_step

pcm_signal = (quantized_signal - min(quantized_signal)) / quantization_step pcm_signal = pcm_signal.astype(int)

plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1) plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue') plt.title("Message Signal (Analog)") plt.xlabel("Time [s]") plt.ylabel("Amplitude") plt.grid(True)

plt.subplot(4, 1, 2) plt.plot(t, clock_signal, label="Clock Signal (Increased Frequency)", color='green') plt.title("Clock Signal (Increased Frequency)") plt.xlabel("Time [s]") plt.ylabel("Amplitude") plt.grid(True)

plt.subplot(4, 1, 3) plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red') plt.title("PCM Modulated Signal (Quantized)") plt.xlabel("Time [s]") plt.ylabel("Amplitude") plt.grid(True)

plt.subplot(4, 1, 4) plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--') plt.title("Signal Without Demodulation") plt.xlabel("Time [s]") plt.ylabel("Amplitude") plt.grid(True)

plt.tight_layout() plt.show()

Output waveform 

![WhatsApp Image 2025-03-27 at 19 59 30_8cee0f57](https://github.com/user-attachments/assets/8a084d7c-695e-4811-bce5-1cd6a07d3def)


Result

The result is a set of plots that visualize the original analog message signal, the clock signal used for sampling, the quantized PCM signal, and the reconstructed signal after demodulation.
