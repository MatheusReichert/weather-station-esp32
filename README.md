# Weather Station — ESP32

Autonomous weather station built with ESP32 that collects environmental data from multiple sensors and publishes it over Wi-Fi via MQTT.

Developed for the **Embedded Systems** course at Instituto Federal Catarinense.

---

## Sensors

| Sensor | Measurement |
|--------|------------|
| DHT22 | Temperature & Humidity |
| BMP085 | Atmospheric Pressure & Altitude |
| ML8511 | UV Radiation |
| Rain Sensor | Rain detection (analog) |
| Rain Gauge | Rainfall accumulation (digital pulse) |
| Anemometer | Wind speed (digital pulse) |
| Wind Vane | Wind direction (N / S / E / W) |

---

## How it works

Every second, the ESP32 reads all sensors and publishes a JSON payload to an MQTT broker over Wi-Fi:

```json
{
  "temperature": "23.5",
  "humidity": "68.0",
  "pressure": "850.0",
  "uv": "0.012",
  "rain": "dry",
  "anemometer_state": "1",
  "rain_gauge_state": "0",
  "wind_vane_north_state": "1",
  "wind_vane_south": "0",
  "wind_vane_west": "0",
  "wind_vane_east": "0"
}
```

---

## Stack

- **Hardware**: Heltec ESP32
- **Framework**: Arduino (via PlatformIO)
- **Language**: C++
- **Protocol**: MQTT (EspMQTTClient)

## Libraries

- [esp32DHT](https://github.com/bertmelis/esp32DHT) — async DHT22 driver
- [EspMQTTClient](https://github.com/plapointe6/EspMQTTClient) — MQTT over Wi-Fi
- [Adafruit BMP085](https://github.com/adafruit/Adafruit-BMP085-Library) — pressure sensor
- [ML8511](https://github.com/RobTillaart/ML8511) — UV sensor
- [Heltec ESP32](https://github.com/HelTecAutomation/Heltec_ESP32) — board support

---

## Getting started

1. Install [PlatformIO](https://platformio.org/)
2. Clone the repo
3. Set your Wi-Fi credentials and MQTT broker address in `src/main.cpp`
4. Flash: `pio run --target upload`

---

## Team

- Andrew de Carvalho Dellamea
- Brendha Iara Gruber de Lima
- Felipe Alves Santana
- Matheus Ernan Reichert
