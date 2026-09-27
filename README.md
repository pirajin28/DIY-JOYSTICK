# DIY Motion Controller 🎮

A DIY wireless motion controller built using an **ESP32**, a **PS2 joystick module**, and an **MPU6050 accelerometer/gyroscope**.

The controller creates its own Wi-Fi network and hosts a web-based racing game directly from the ESP32. No router, internet connection, or external server is required.

---

## 🚀 Features

- ESP32-powered wireless controller
- PS2 joystick for movement and acceleration
- Joystick button for boost/restart
- MPU6050 motion sensor for steering
- ESP32 creates its own Wi-Fi hotspot
- Browser-based racing game
- No internet or router required
- Real-time controller data sent to the game
- Traffic cars, trees, sunset sky, clouds and increasing difficulty
- Boost system with recharge timer
- Game-over and high-score system

---

## 🧰 Hardware Required

- ESP32 DevKit V1
- PS2 joystick module
- MPU6050 module
- Breadboard
- Jumper wires
- USB cable
- Computer or phone with a web browser

---

# 🔌 Connections

## PS2 Joystick Module → ESP32

| Joystick Pin | ESP32 Pin |
|---|---|
| GND | GND |
| 5V | 3V3 |
| VRx | GPIO 34 |
| VRy | GPIO 35 |
| SW | GPIO 25 |

> ⚠️ **Important:** The joystick module's `5V` pin is connected to the ESP32's **3V3 pin** in this project. This keeps the joystick's analog output within a safe voltage range for the ESP32 ADC.

### Joystick orientation

When connecting the joystick, hold the joystick module so that the **lettering is straight/upright and the connection pins are on the left side**.

This orientation is important when following the X/Y directions described in the project.

---

## MPU6050 → ESP32

| MPU6050 Pin | ESP32 Pin |
|---|---|
| VCC | 3V3 |
| GND | GND |
| SCL | GPIO 22 |
| SDA | GPIO 21 |
| XDA | Not connected |
| XCL | Not connected |
| AD0 | Not connected |
| INT | Not connected |

The MPU6050 uses I²C communication.

---

# 📡 Connecting to the Controller

The ESP32 creates its own Wi-Fi network.

**Wi-Fi Name:** `DIY-MOTION`  
**Password:** `DIYMOTION2026`

After connecting to the ESP32's Wi-Fi, open:

`http://192.168.4.1`

No internet connection or external router is required.

The phone or computer communicates directly with the ESP32.

---

# 🎮 Controls

### Joystick

- **Left** → Steer left
- **Right** → Steer right
- **Up** → Accelerate
- **Down** → Brake
- **Joystick button (SW)** → Boost

The joystick button can also be used to restart the game after a game over.

### MPU6050

The motion sensor provides additional steering input by tilting/moving the controller.

---

# 🏎️ The Game

The ESP32 hosts the racing game directly.

The browser loads the game from:

`http://192.168.4.1`

When the controller is connected, the game continuously receives live joystick and MPU6050 data from the ESP32.

The game includes:

- Two-lane road
- Blue player car
- Red traffic cars
- Moving roadside trees
- Animated sunset
- Animated clouds
- Increasing difficulty
- Collision detection
- Score system
- Best-score storage
- Game-over screen
- Boost system

---

# ⚡ Boost System

Pressing the joystick button activates the boost.

- Boost lasts for **5 seconds**
- After boost ends, a **10-second recharge** begins
- Boost cannot be activated again until the recharge is complete
- The recharge status is displayed on the game HUD

---

# 🛠️ How It Works

The ESP32 performs three main jobs:

1. Reads the joystick.
2. Reads the MPU6050.
3. Hosts the Wi-Fi network and web server.

The controller sends the sensor data to the browser through:

`/data`

The browser then uses that data to control the racing game.

---

# 📶 Network

The ESP32 works as a Wi-Fi Access Point.

This means the controller does **not** need to connect to an existing Wi-Fi router.

The connection looks like:

**Joystick + MPU6050 → ESP32 → Wi-Fi → Phone/PC → Browser Game**

The Wi-Fi network is local to the ESP32.

---

# 📁 Project Structure

The main ESP32 sketch contains the controller firmware and the web server.

The game is served directly by the ESP32 when the browser connects to:

`http://192.168.4.1`

---

# 🔧 Setup

1. Install the Arduino IDE.
2. Install ESP32 board support.
3. Select **ESP32 Dev Module**.
4. Connect the ESP32 using USB.
5. Upload the `.ino` file.
6. Keep the controller still during startup so the sensor/joystick calibration can complete.
7. Connect your phone or computer to:

   `DIY-MOTION`

8. Enter the password:

   `DIYMOTION2026`

9. Open:

   `http://192.168.4.1`

10. Start the race!

---

# 📜 License

This project is made as a DIY/hobby electronics project.

Feel free to build your own version and modify the hardware, software and game.

---

# 👨‍💻 DIY Motion Controller

Built using:

- ESP32
- PS2 Joystick Module
- MPU6050
- Arduino
- HTML / CSS / JavaScript
- Wi-Fi