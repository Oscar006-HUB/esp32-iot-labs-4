# ESP32 IoT Labs (Labs 2–6)

ESP32 sensor firmware and Python/Flask dashboards for an end-to-end IoT measurement pipeline (DHT11, LDR, HC-SR04 → MQTT → web dashboard).

## Architecture

```
ESP32 sensors ──MQTT──▶ Broker (Mosquitto / HiveMQ) ──▶ Flask + Plotly dashboard
(DHT11, LDR, HC-SR04)                                   (live charts, CSV export)
```

## Contents

| Path | Description |
|------|-------------|
| `lab 2-6  arduino code/esp-code/esp-code.ino` | ESP32 firmware: DHT11 (GPIO 18), LDR (GPIO 34), HC-SR04 (Trig 4 / Echo 23), JSON over MQTT |
| `lab2_code/lab2_code.ino` | Lab 2 sketch: DHT11 → MQTT |
| `(lab3)mqtt_server.py` | Lab 3: minimal Flask + MQTT subscriber |
| `lab4.py`, `app.py` | Flask dashboard with live data API (`/api/data`) and CSV download (`/download`) |
| `lab5.py`, `lab6.py` | Later lab iterations of the dashboard |
| `RUNECRAFT_report.csv` | Sample exported sensor readings |

## Running the dashboard

```bash
pip install flask paho-mqtt plotly dash
python app.py
```

`app.py` reads `MQTT_BROKER` and `MQTT_PORT` from environment variables (default `broker.hivemq.com:1883`).

## Configuration

WiFi credentials are **not** committed. Before flashing, replace the placeholders in the sketch:

```cpp
const char* ssid     = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";
```

Also set `mqtt_server` to the IP address of the machine running your MQTT broker.

---

Author: **Prince Oscar Mwinnuo** ([@Oscar006-HUB](https://github.com/Oscar006-HUB))
