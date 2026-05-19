# 🔌 Project 3 — 2-to-4 Decoder: Room/Channel Selector

![Difficulty](https://img.shields.io/badge/Difficulty-⭐⭐-yellow)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![IC](https://img.shields.io/badge/IC-SN74LS139N-blue)

A hardware logic circuit that takes a **2-bit binary input** and activates **exactly one of 4 LEDs** — built using the SN74LS139N dual 2-to-4 decoder IC.

---

## 📌 What It Does

Given a 2-bit input (A, B) via DIP switches, the circuit lights up one specific LED out of four. This mimics real-world applications like:

- **Memory address decoding** — selecting one memory chip out of four
- **Channel selection** — routing a signal to one of N outputs
- **Multiplexed display control** — activating one segment group at a time

---

## 🧰 Components Used

| Component | Value / Part No. | Qty |
|---|---|---|
| Decoder IC | SN74LS139N | 1 |
| LEDs | Any color | 4 |
| Resistors | 1kΩ (current limiting) | 4 |
| Resistors | 10kΩ (pull-down) | 2 |
| DIP Switch | 8-position | 1 |
| Breadboard | — | 1 |
| Jumper Wires | — | Several |
| Power Supply | 5V DC | 1 |

---

## 🔧 Circuit Connections

### Power
| IC Pin | Connect To |
|---|---|
| Pin 16 (VCC) | +5V |
| Pin 8 (GND) | GND |
| Pin 1 (~E) | GND (enables decoder) |

### Input Switches (A & B)
Each switch is wired with a **10kΩ pull-down resistor** to ensure a clean LOW when the switch is off.

```
+5V → DIP Switch position 1 → IC Pin 2 (A)
                               IC Pin 2 → 10kΩ → GND

+5V → DIP Switch position 2 → IC Pin 3 (B)
                               IC Pin 3 → 10kΩ → GND
```

### Output LEDs (Active LOW)
Outputs are active LOW — LED lights when the output pulls LOW.

```
+5V → 1kΩ resistor → LED anode (+, long leg)
LED cathode (−, short leg) → IC Output Pin
```

| IC Pin | Output | LED |
|---|---|---|
| Pin 7 | ~Y0 | LED0 |
| Pin 6 | ~Y1 | LED1 |
| Pin 5 | ~Y2 | LED2 |
| Pin 4 | ~Y3 | LED3 |

---

## 📊 Truth Table

| SW-B (Pin 3) | SW-A (Pin 2) | Active Output | LED ON |
|:---:|:---:|:---:|:---:|
| 0 (OFF) | 0 (OFF) | ~Y0 LOW | LED0 |
| 0 (OFF) | 1 (ON) | ~Y1 LOW | LED1 |
| 1 (ON) | 0 (OFF) | ~Y2 LOW | LED2 |
| 1 (ON) | 1 (ON) | ~Y3 LOW | LED3 |

---

## ⚠️ Key Notes

- **Pin 1 (~E) must be tied to GND** — it's active LOW enable. If left floating, the IC won't decode anything.
- **Pull-down resistors are mandatory** on input pins — without them, floating pins cause random/stuck outputs.
- **LEDs are reverse-connected** compared to typical circuits — anode goes to VCC, cathode goes to IC output (because outputs are active LOW).
- Only **Decoder 1** of the SN74LS139N is used (pins 1–7). Decoder 2 (pins 9–15) is left unconnected.

---

## 🚀 How to Replicate

1. Place SN74LS139N on breadboard across the center gap
2. Connect Pin 16 → +5V, Pin 8 → GND, Pin 1 → GND
3. Wire DIP switch positions 1 & 2 with pull-down resistors to IC pins 2 & 3
4. Connect 4 LEDs with 1kΩ resistors between VCC and IC output pins 4–7
5. Power on — flip switches and watch exactly one LED respond

---

## 📚 What I Learned

- How a 2-to-4 decoder works at the hardware level
- Active LOW logic and how to wire LEDs accordingly
- Importance of pull-down resistors on floating input pins
- Real-world use of decoder ICs in address/channel selection

---

## 📁 Folder Structure

```
2-to-4-decoder/
├── README.md
├── images/
│   ├── circuit_photo.jpg       ← your breadboard photo
│   └── wiring_diagram.png      ← diagram screenshot
└── notes/
    └── observations.txt        ← optional personal notes
```

---

*Part of an ongoing electronics lab series — building circuits from scratch using 74LS series logic ICs.*
