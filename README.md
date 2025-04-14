# EXP.NO.9-Simulation-of-Pulse-Code-Modulation
9.Simulation of PCM

# AIM
To implement Pulse Code Modulation (PCM) for encoding and decoding a sinusoidal signal using quantization and to observe the output waveforms.

# SOFTWARE REQUIRED
google colab

# ALGORITHMS
Generate an analog signal (e.g., a sine wave). Define a sampling rate and generate sampled data points. Choose a number of quantization levels and perform quantization on the sampled data. Convert the quantized levels to binary representations (this is the encoding step). (Optional for visualization) Simulate a basic reconstruction by plotting the quantized levels as a step function.

# PROGRAM
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

# OUTPUT
![image](https://github.com/user-attachments/assets/6d570663-02b7-4969-a846-6321a41ff3fe)



 
# RESULT / CONCLUSIONS
Pulse Code Modulation (PCM) converts analog signals into digital form by sampling and quantizing the signal. The result is a series of pulses that represent the digitized version of the original signal, widely used in audio and telecommunications.
