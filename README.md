# EXPERIMENT 7: SPECTRAL ANALYSIS, SPECTRAL DENSITY AND TIME-INVARIANT LINEAR FILTERS
# NAME: MONISHA
# REG NO: 2305001019

## Aim
To perform spectral analysis on a simulated time series, identify dominant frequencies using a periodogram, apply a moving-average filter, and compare the spectral density before and after filtering.

## Objectives
1. To generate a time series containing multiple frequencies and random noise.
2. To calculate and plot the periodogram.
3. To identify the dominant frequency in the time series.
4. To apply a moving-average linear filter.
5. To compare the original and filtered time series.
6. To study the effect of changing the signal frequency, filter window size, and noise.
7. To observe the effect of adding another frequency component.

## Software Required
- Python 3
- NumPy
- Matplotlib
- SciPy

## Procedure
1. Import the required libraries.
2. Generate time points and a time series containing two frequencies and random noise.
3. Plot the original time series.
4. Calculate and plot the periodogram.
5. Identify the dominant frequency.
6. Apply a 5-point moving-average filter.
7. Compare the original and filtered time series.
8. Compare spectral density before and after filtering.
9. Change the frequency, increase the filter window to 10, remove noise, and add another frequency component.
 
##  program 
```
# EXPERIMENT 7: SPECTRAL ANALYSIS AND LINEAR FILTERS

import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

# Step 1: Generate time points
n = 500
t = np.arange(n)

# Step 2: Generate a time series with two frequencies and noise
np.random.seed(42)

x = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.random.randn(n)
)

# Step 3: Plot the original time series
plt.figure(figsize=(10, 4))
plt.plot(t, x)
plt.title("Original Time Series")
plt.xlabel("Time")
plt.ylabel("Value")
plt.grid(True)
plt.show()

# Step 4: Calculate and plot the periodogram
frequency, power = signal.periodogram(x)

plt.figure(figsize=(10, 4))
plt.plot(frequency, power)
plt.title("Spectral Density of Original Time Series")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()

# Step 5: Identify the dominant frequency
peak_index = np.argmax(power[1:]) + 1
dominant_frequency = frequency[peak_index]

print("Dominant Frequency:", dominant_frequency)

# Step 6: Apply a 5-point moving-average filter
window = 5
filtered = np.convolve(
    x, np.ones(window) / window, mode="same"
)

# Step 7: Compare original and filtered time series
plt.figure(figsize=(10, 4))
plt.plot(t, x, label="Original")
plt.plot(t, filtered, label="Filtered")
plt.title("Original vs Filtered Time Series")
plt.xlabel("Time")
plt.ylabel("Value")
plt.legend()
plt.grid(True)
plt.show()

# Step 8: Compare spectral density before and after filtering
f_original, p_original = signal.periodogram(x)
f_filtered, p_filtered = signal.periodogram(filtered)

plt.figure(figsize=(10, 4))
plt.plot(f_original, p_original, label="Original")
plt.plot(f_filtered, p_filtered, label="Filtered")
plt.title("Spectral Density Before and After Filtering")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.legend()
plt.grid(True)
plt.show()

# Task 1: Change frequency from 0.05 to 0.10
x_task1 = (
    np.sin(2 * np.pi * 0.10 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.random.randn(n)
)

f_task1, p_task1 = signal.periodogram(x_task1)

plt.figure(figsize=(10, 4))
plt.plot(f_task1, p_task1)
plt.title("Task 1: Effect of Changing Frequency")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()

# Task 2: Change window size to 10
window = 10
filtered_task2 = np.convolve(
    x, np.ones(window) / window, mode="same"
)

plt.figure(figsize=(10, 4))
plt.plot(t, x, label="Original")
plt.plot(t, filtered_task2, label="Filtered (Window = 10)")
plt.title("Task 2: Effect of Increasing Filter Window")
plt.xlabel("Time")
plt.ylabel("Value")
plt.legend()
plt.grid(True)
plt.show()

# Task 3: Generate a signal without noise
x_task3 = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
)

f_task3, p_task3 = signal.periodogram(x_task3)

plt.figure(figsize=(10, 4))
plt.plot(f_task3, p_task3)
plt.title("Task 3: Spectral Density Without Noise")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()

# Task 4: Add another frequency component
x_task4 = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.sin(2 * np.pi * 0.30 * t)
    + 0.3 * np.random.randn(n)
)

f_task4, p_task4 = signal.periodogram(x_task4)

plt.figure(figsize=(10, 4))
plt.plot(f_task4, p_task4)
plt.title("Task 4: Spectral Density with an Additional Frequency")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()
```

## Expected Output
- Original time-series graph.
  <img width="1085" height="450" alt="image" src="https://github.com/user-attachments/assets/0dcc982e-94e3-41d7-a8d0-eb1b9415fd29" />

- Spectral density of the original time series.
  <img width="1057" height="512" alt="image" src="https://github.com/user-attachments/assets/a28c3a4a-0b9a-42d3-8d51-0814132ec26f" />

- Dominant frequency.
  <img width="292" height="48" alt="image" src="https://github.com/user-attachments/assets/0dd9c6f6-c31f-48e7-b6c9-4a48b08fe894" />

- Original versus filtered time-series graph.
  <img width="1102" height="500" alt="image" src="https://github.com/user-attachments/assets/4b011ca7-7a8d-4556-8f8d-170d8e89f650" />

- Spectral density before and after filtering.
  <img width="1096" height="497" alt="image" src="https://github.com/user-attachments/assets/6d386706-295f-4db2-ba58-0b0939d7c1c3" />

- Graphs showing the effects of changing frequency, filter window, noise, and additional frequency components.
  <img width="1113" height="492" alt="image" src="https://github.com/user-attachments/assets/efacd5ac-554f-4c49-9552-08e2683b58d3" />
  <img width="1097" height="486" alt="image" src="https://github.com/user-attachments/assets/03253218-3d73-4600-9354-5e37eda737d2" />
  <img width="1098" height="507" alt="image" src="https://github.com/user-attachments/assets/283aab8b-9317-4e91-bdd8-ab5e6ba6422d" />
  <img width="1153" height="508" alt="image" src="https://github.com/user-attachments/assets/c2a279b4-534b-4553-a47d-b3498cc9dda7" />
  
## Result
Spectral analysis was performed successfully using the periodogram to identify dominant frequencies. A moving-average filter was applied to smooth the time series, and the spectral density before and after filtering was compared. The effects of changing frequency, removing noise, increasing the filter window, and adding another frequency component were studied.
