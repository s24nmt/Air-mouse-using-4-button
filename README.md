# Air-mouse-using-4-button
This firmware turns a Seeed Studio XIAO ESP32-C6 and an MPU6050 6-axis motion sensor into a 125Hz Bluetooth Low Energy (BLE) Air Mouse with physical click/scroll buttons, battery telemetry, and an 8-LED WS2812B status strip.
Open Arduino IDE (v2.x recommended) and go to File → Preferences (on macOS: Arduino IDE → Settings).

In Additional boards manager URLs, paste this link (if you already have URLs there, click the icon on the right and add it on a new line):

Plaintext
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
Install Required Libraries
Your sketch uses three external libraries:

Via Library Manager (Tools → Manage Libraries):

Search for MPU6050_tockn and install MPU6050_tockn by tockn.

Search for Adafruit NeoPixel and install Adafruit NeoPixel by Adafruit.

Via ZIP Import (for BLE HID Mouse):

Download the HijelHID_BLEMouse repository as a .zip file from GitHub.

In Arduino IDE, go to Sketch → Include Library → Add .ZIP Library... and select the downloaded .zip file. (If prompted for dependencies during compile, also install NimBLE-Arduino from the Library Manager.)

Configure Board & Upload Settings
BoardXIAO_ESP32C6Under Tools → Board → esp32PortSelect your active COM / USB portAppears when the board is plugged inUSB CDC On BootEnabledRequired to see gyro calibration & battery logs in Serial MonitorPartition SchemeHuge APP (3MB No OTA/1MB SPIFFS)Prevents "Sketch too big" errors caused by the BLE stackUpload Speed921600Standard fast flashing speed (drop to 115200 if uploads fail)
