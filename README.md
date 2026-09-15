# 🚗 Automatic Headlight & Indicator System — STM32

> **STM32-based automotive lighting system** that reads analog voltage from a potentiometer and automatically controls LEDs based on predefined ADC voltage ranges — simulating real-world headlight and indicator behavior.

---

## 📌 Overview

An embedded automotive system that uses an **STM32F103C8T6 microcontroller** to read analog voltage from a 10 kΩ potentiometer and control three LEDs based on predefined ADC voltage ranges. The system simulates automatic headlight dimming and indicator switching in response to real-time analog input changes.

---

## 🎯 Objective

To interface a potentiometer as an analog input with the STM32 microcontroller and control three LEDs according to different ADC voltage ranges, simulating an **automatic headlight and indicator system**.

---

## 🔧 Hardware Components

| Component | Description |
|-----------|-------------|
| STM32F103C8T6 Blue Pill | Main microcontroller |
| 10 kΩ Potentiometer | Analog voltage source (simulates light/position sensor) |
| Red LED | Indicator / brake light simulation |
| Green LED | Safe / normal headlight indication |
| Blue LED | High beam / alternate indicator |
| 330 Ω Resistors | Current limiting for LEDs |
| Connecting Wires | Circuit connections |

---

## ⚙️ System Architecture

```
Potentiometer (10kΩ)
        │
        ▼
  ADC Input (PA0)
        │
        ▼
STM32F103C8T6
        │
        ▼
  Voltage Range Check
        │
   ┌────┼────┐
   │    │    │
Range1 Range2 Range3
   │    │    │
 Red  Green Blue
 LED   LED   LED
```

---

## 🔄 Working

The potentiometer generates a variable analog voltage (0V to 3.3V) based on its rotational position. The STM32 ADC (12-bit resolution) converts this into a digital value (0–4095) and processes it to control LEDs:

| ADC Range | Voltage Range | LED State |
|-----------|--------------|-----------|
| 0 – 1365 | 0V – 1.1V | 🔴 Red LED ON |
| 1366 – 2730 | 1.1V – 2.2V | 🟢 Green LED ON |
| 2731 – 4095 | 2.2V – 3.3V | 🔵 Blue LED ON |

The system responds in **real time** to potentiometer position changes.

---

## 🛠️ Technologies Used

- **Microcontroller:** STM32F103C8T6 (Blue Pill)
- **Programming Language:** Embedded C
- **Peripherals:** ADC, GPIO
- **Concepts:** Analog Signal Processing, LED Interfacing, Voltage Range Detection, Real-Time Control

---

## 🔌 Circuit Connections

| Component | STM32 Pin |
|-----------|-----------|
| Potentiometer AOUT | PA0 (ADC Input) |
| Potentiometer VCC | 3.3V |
| Potentiometer GND | GND |
| Red LED | PB0 |
| Green LED | PB1 |
| Blue LED | PB2 |

---

## ✅ Results

- STM32 successfully converted potentiometer analog voltage into 12-bit digital values
- LEDs responded correctly to predefined ADC voltage ranges
- System responded in **real time** to changes in potentiometer input
- Smooth and accurate transition between LED states at voltage thresholds
