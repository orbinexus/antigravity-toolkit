---
name: iot-esp32-maker
description: Designs IoT hardware firmwares, circuits, sensors integrations, and WebSockets/MQTT web dashboards for ESP32, ESP8266, Arduino, and Raspberry Pi in C++ and MicroPython.
---

# IoT & ESP32 Smart Device Maker

This skill guides the design of micro-firmware, pinouts, circuit logic, and real-time telemetry dashboards for ESP32/Arduino embedded devices.

## 1. Embedded Firmware Guidelines

1. **Non-Blocking Execution**:
   - Strictly prohibit long `delay()` calls in the main `loop()`.
   - Use `millis()` timers or FreeRTOS tasks (`xTaskCreatePinnedToCore`) for asynchronous scheduling.
2. **Network & Recovery Resilience**:
   - Include auto-reconnect loops for Wi-Fi and MQTT brokers with exponential backoff.
   - Implement watchdog timers (`esp_task_wdt`) to auto-reboot frozen hardware safely.
3. **Power Management**:
   - For battery-operated devices, use deep sleep modes (`esp_deep_sleep_start()`) triggered by timer or capacitive touch GPIO wakes.

## 2. Real-Time Telemetry & Control

- Expose local lightweight async web servers (`ESPAsyncWebServer`) with captive portals for easy Wi-Fi configuration.
- Transmit sensor telemetry via MQTT JSON payloads or WebSocket streams for lag-free local web dashboards.
