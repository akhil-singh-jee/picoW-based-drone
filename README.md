# 🛩️Raspberry Pi Pico-W Based Mini Drone  

## Project Overview
This project is a Raspberry Pi Pico W–based mini drone designed for hands-on experimentation with wireless control, sensor fusion, and flight stabilization. It uses coreless DC motors, an MPU-6050 gyroscope and accelerometer, and a Li-Po battery powered through a DC-DC boost converter. The drone connects to a mobile app via Wi-Fi for real-time flight control and telemetry.
The total build weight is approximately 210 grams, making it lightweight and suitable for indoor and short-range outdoor flight tests, controlled wirelessly via the custom **AirM Mobile App (v1.1)**.

---

![Drone Prototype](https://github.com/akhil-singh-jee/picoW-based-drone/blob/main/Images/Prototype%20picoW%20Drone.jpg)

## All Components List

| Component | Specification | Quantity | Description |
|------------|----------------|-----------|--------------|
| **DC Coreless Motors** | 50,000 – 60,000 RPM, 3.7 – 4.2 V, 55 mm | 4 | Lightweight high-speed propulsion motors |
| **Propellers** | 55 mm (compatible with motor shaft) | 4 | Two CW + Two CCW blades |
| **MPU-6050 Sensor Module** | 3-axis Gyroscope + Accelerometer, 16-bit AD Converter, ±250 – ±2000 dps | 1 | Provides motion and orientation data |
| **Resistors (SMD 1206)** | 1 kΩ and 10 kΩ | As needed | Used for pull-up/pull-down and circuit balancing |
| **Male & Female Pins** | Standard 2.54 mm | As needed | For modular and flexible connections |
| **Power Booster Module (MT3608)** | DC-DC Step-Up Converter, Adjustable Output | 1 | Boosts 3.7 V Li-Po to 5 V for Pico and motors |
| **Li-Po Battery** | 3.7 V, 300 mAh | 1 | Lightweight rechargeable power source |
| **Raspberry Pi Pico W** | Dual-core RP2040, Wi-Fi enabled | 1 | Drone’s main controller |
| **Breadboard** | Mini breadboard | 1 | For initial circuit testing and prototyping |
| **LED Indicator** | 3 mm / 5 mm (red or blue) | 1 | Indicates charging or power status |
| **Push Button Switch** | Momentary type | 1 | Used for manual control or charging on/off function |


### Some extra tools/parts used in the project:
	
1.	3D printer.
2.	Hot air gun.
3.	ScrewDriver kit.
4.  Soldering iron gun & paste.


---
![PicoW Drone ](https://github.com/akhil-singh-jee/picoW-based-drone/blob/main/Images/PicoW2.jpg)

## Circuit & Connections

**Main connections:**
- **MPU-6050** → I²C Bus (SDA → GPIO 0, SCL → GPIO 1)  
- **Motors** → PWM Pins (GPIO 2–5 for 4 motors) via transistor drivers  
- **MT3608 Output → Pico 5 V (VBUS)**  
- **Li-Po Battery → MT3608 Input**  
- **LED → GPIO 15** (with 220 Ω resistor)  
- **Button → GPIO 14** (pulled low when pressed)  
- Common Ground (GND) across all modules
- Circuit diagram (Not Available).

![MPU6050](https://github.com/akhil-singh-jee/picoW-based-drone/blob/main/Images/MPU6050.jpg)

---

## Control System – AirM App v1.1 (Andriod App)

The **AirM Mobile App** (Android) connects to the Pico W via Wi-Fi.

**App Features:**
- Real-time throttle, pitch, yaw, and roll control  
- Live gyro feedback display  
- Wi-Fi Direct / Hotspot connection  
- Optional telemetry via MQTT or HTTP  

**Communication:**  
Uses **UDP/TCP packets** between the AirM App and Pico W firmware.



---

## Firmware (Raspberry Pi Pico W)

**Language:** MicroPython / C++  

### Tasks:
1. Connect to Wi-Fi network (AirM App Hotspot)  
2. Read MPU-6050 data (gyro + accel)  
3. Compute PID for stabilization  
4. Control motor PWM outputs  
5. Receive commands via socket communication  

#### firmware is self-designed with company support, optimized for efficient motor response and stable flight performance.



---

## Acknowledgment

Special thanks to [AirM](https://airm.co.in) for providing technical guidance, resources, and development support throughout the design and testing of this project. Their expertise in drone technology and embedded systems made this innovation possible.
