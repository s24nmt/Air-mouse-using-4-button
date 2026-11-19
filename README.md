# Air-mouse-using-4-button
This firmware turns a Seeed Studio XIAO ESP32-C6 and an MPU6050 6-axis motion sensor into a 125Hz Bluetooth Low Energy (BLE) Air Mouse with physical click/scroll buttons, battery telemetry, and an 8-LED WS2812B status strip.
Hardware & Communication Architecture
Microcontroller & BLE HID: Runs on the XIAO ESP32-C6 using the HijelHID_BLEMouse library, operating at a 125Hz update rate (8ms loop interval) for responsive wireless cursor control.
High-Speed I2C Sensor Bus: Communicates with the MPU6050 gyroscope over I2C (SDA on D4/GPIO 22, SCL on D5/GPIO 23) at 400kHz Fast Mode to minimise sensor read latency.
Addressable RGB Feedback: Drives an 8-LED WS2812B NeoPixel strip on D2 (GPIO 2), capped at 60/255 brightness to balance visibility with battery life.
Multi-Function 4-Button ControlsAll four push buttons use internal pull-up resistors (INPUT_PULLUP) and software timing logic:
ButtonPinShort PressLong Press / HoldExtra BehaviourButton 1D1Left Click (30ms debounced)Click & Drag (holds left button down until released)Triggers 70ms cursor freeze on press; auto-releases on disconnect or sleep.Button 2D3Right Click (30ms to 500ms press)Middle Click (triggers at 500ms)Precision Mode: Halves cursor sensitivity (0.08 → 0.04) while held down.Button 3D6Turn LEDs ON (30ms debounced)—Re-enables the RGB strip and immediately sets it to solid blue.Button 4D7Turn LEDs OFF (under 250ms)Gyro Air Scroll (hold ≥ 250ms and tilt up/down)Releasing after scrolling exits scroll mode without turning off the LEDs.
