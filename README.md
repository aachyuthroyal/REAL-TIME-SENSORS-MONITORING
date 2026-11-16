# Real-Time Sensor Monitoring station Using Periodic Task Scheduler

![Language](https://img.shields.io/badge/Language-Embedded%20C-blue)
![MCU](https://img.shields.io/badge/MCU-LPC2129%20ARM7-green)
![Interface](https://img.shields.io/badge/Interface-UART%209600%20Baud-orange)

> Real-time monitoring of 5 sensors on LPC2129 using a Periodic Task Scheduler. Live sensor data is transmitted to Linux Terminal over UART and local alerts are given via LED / Buzzer.

---
*LPC2129 Sensor Station* monitors 5 sensor inputs continuously without blocking.
Each sensor is sampled periodically by the scheduler, safety limits are checked, and data is sent to a Computer via UART.
## 🛠️ Hardware Used

| Component | Description |
| :--- | :--- |
| *LPC2129* | ARM7TDMI-S Based Microcontroller |
| *Temp Sensor* | LM35 / Thermistor - Analog |
| *LDR Sensor* | Light Intensity - Analog |
| *Potentiometer* | Variable Voltage - Analog (ADC) |
| *Vibration Sensor* | Digital - Vibration Detection |
| *Flame Sensor* | Digital - Flame Detection |
| *LED / Buzzer* | Local Alarm Output - GPIO |
| *UART Cable* | LPC2129 to PC Communication |

## 📌 Project Overview

**LPC2129 Sensor Station** monitors 5 sensor inputs continuously without blocking.
Each sensor is sampled periodically by the scheduler, safety limits are checked, and data is sent to a Computer via UART.

No `delay()` - All tasks run on fixed time periods.

---

## 🏗️ System Architecture

### Project Block Diagram
TEMP SENSOR ─┐
  LDR SENSOR ──┤
  POT ─────────┼──> [ LPC2129 MCU ] ──> UART INTERFACE ──> COMPUTER / Linux Terminal
  VIBRATION ───┤           │
  FLAME SENSOR ┘           └──> LED / BUZZER (GPIO)javascript
### How It Works

1.  **5 Sensor Inputs:** Temperature, Light (LDR), Potentiometer, Vibration, and Flame sensors connect directly to LPC2129.
2.  **LPC2129 Microcontroller:** Reads analog channels via ADC, checks digital inputs, and monitors safety limits.
3.  **Serial Data Output:** Transmits live sensor readings to the Linux terminal continuously over UART at 9600 baud.
4.  **Local Alarm Output:** Controls status LED and buzzer on GPIO to give immediate warnings when limits are crossed.

---

## 🛠️ Hardware Used

| Component | Description |
| :--- | :--- |
| **LPC2129** | ARM7TDMI-S Based Microcontroller |
| **Temp Sensor** | LM35 / Thermistor - Analog |
| **LDR Sensor** | Light Intensity - Analog |
| **Potentiometer** | Variable Voltage - Analog (ADC) |
| **Vibration Sensor** | Digital - Vibration Detection |
| **Flame Sensor** | Digital - Flame Detection |
| **LED / Buzzer** | Local Alarm Output - GPIO |
| **UART Cable** | LPC2129 to PC Communication |

---

## 💻 Software / Tools Used

- **Language:** Embedded C
- **IDE:** Keil uVision / LPCXpresso
- **Terminal:** Linux Terminal / TeraTerm / PuTTY
- **Protocol:** UART @ 9600 Baud, 8-N-1
- **Scheduler:** Custom Periodic Task Scheduler

---

## ⏱️ Periodic Task Scheduler

| Task Name | Period | Priority | Function |
| :--- | :--- | :--- | :--- |
| `TempTask` | 1000 ms | High | Read Temperature via ADC |
| `LightTask` | 500 ms | Medium | Read LDR - Light % |
| `PotTask` | 500 ms | Low | Read Pot - Voltage % |
| `VibrationTask` | 200 ms | High | Check Vibration - YES / NO |
| `FlameTask` | 200 ms | High | Check Flame - YES / NO |
| `UARTTask` | 1000 ms | Medium | Send Data to Linux Terminal |
| `AlarmTask` | 100 ms | High | LED / Buzzer if Limit Crossed |

---
🚀 How To Run
1. Clone Repobashgit clone https://github.com/your-username/Real-Time-Sensor-Monitoring-LPC2129.git2. Build in Keil uVision
Open Project in Keil uVisionTarget: LPC2129Build (F7) -> Generate .hex3. Flash & Run
Flash .hex to LPC2129 using Flash MagicConnect UART to PCOpen Linux Terminal:bashsudo minicom -D /dev/ttyUSB0 -b 9600
# OR
sudo screen /dev/ttyUSB0 9600📊 Sample Output - Linux TerminaljavascriptOn the Linux TERMINAL
TEMP: 28 C
LIGHT: 50%
VTG: 3.3% (MAX)
VIBRATIONS: NO
FLAME: NO

TEMP: 32 C
LIGHT: 45%
VTG: 3.1%
VIBRATIONS: YES -> ALERT!
FLAME: NO🚨 Alarm ConditionsConditionActionTemp > ThresholdLED ON + Buzzer ONFlame DetectedLED ON + Buzzer ONVibration DetectedLED Blink + Buzzer ONNormalLED OFF, Buzzer OFF
🎯 Applications
Industrial Safety MonitoringFire & Vibration Detection SystemSmart Environment MonitoringEmbedded Systems / RTOS Learning ProjectLab Sensor Station
🔮 Future Scope
IoT Cloud DashboardSD Card Data LoggingWireless Monitoring (ESP8266 / Bluetooth)FreeRTOS Porting
