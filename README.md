# Smart-Parking-ESP8266-IR-LCD-Blynk
Smart parking system using NodeMCU (ESP8266), IR sensors, LCD, servo gate control and ultrasonic smart-dustbin monitoring with optional Blynk app integration.
# Smart Parking & Smart Dustbin System using ESP8266, IR Sensors, LCD & Blynk 🚗🅿️🗑️

This project implements a **Smart Parking System** with **automatic gate control** and **parking slot counting**, along with a **Smart Dustbin level monitor**, using:

- **NodeMCU (ESP8266)**
- **2× IR sensors** at the gate
- **Servo motor** for gate control
- **16x2 I2C LCD**
- **Ultrasonic sensor** for dustbin level
- **Blynk** mobile app (optional – works even if Wi-Fi is disconnected)

The system only opens the gate if parking slots are available and shows the current slot count on the LCD. The dustbin fullness is monitored and sent to Blynk, which can trigger an alert when the dustbin is almost full.

---

## ✨ Features

### Smart Parking

- Two IR sensors at the gate:
  - **IR1** (before gate) → detects vehicle at entrance
  - **IR2** (after gate) → detects vehicle after passing gate
- **Automatic gate control** with a servo motor:
  - Gate opens only if `availableSlots > 0`
  - If parking is full → gate remains closed
- **Automatic slot update**:
  - Vehicle enters → `availableSlots--`
  - Vehicle exits → `availableSlots++`
- **Real-time LCD display** showing:
  - Gate status (Open / Closed)
  - Number of available slots

### Smart Dustbin

- Ultrasonic sensor measures dustbin level
- Calculates **fullness percentage**
- Sends dustbin level to Blynk app
- Triggers an alert in Blynk when dustbin is ≥ 80% full

### Connectivity & Offline Mode

- Uses **Blynk** for:
  - Slot count (V0)
  - Dustbin fullness (V2)
  - Dustbin full alert (V3)
  - Gate status text (V4)
- If Wi-Fi disconnects:
  - System **continues to work locally**
  - Automatically attempts Wi-Fi reconnect every 10 seconds

---

## 🧰 Hardware Required

| Component            | Qty |
|----------------------|:---:|
| NodeMCU ESP8266      |  1  |
| IR Sensor Module     |  2  |
| 16x2 LCD + I2C module|  1  |
| Servo Motor (Gate)   |  1  |
| Ultrasonic Sensor    |  1  |
| Jumper Wires         |  –  |
| 5V Power Supply      |  –  |

---

## 🔌 Pin Connections (as per code)

### ESP8266 (NodeMCU)

```text
IR1        -> D5 (GPIO14)
IR2        -> D6 (GPIO12)
Servo      -> D4 (GPIO2)

Ultrasonic TRIG -> D7 (GPIO13)
Ultrasonic ECHO -> D8 (GPIO15)

LCD I2C   -> SDA = D2, SCL = D1
