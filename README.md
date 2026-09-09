# HID + 400Hz analog + RS-485

Firmware releases for the Waveshare ESP32-S3-ETH linecard personality `hid.mbus485.pwm`.
Source and build instructions: [esp32-aes-gw](https://github.com/fsedano/esp32-aes-gw).

This personality combines the existing USB HID module and RS-485 discrete I/O module with the **400Hz analog** bench output on GPIO1.
The analog amplitude ramps automatically from 0% to 100% in five seconds and
back to 0% in five seconds, using a 100 kHz PWM carrier. Connect GPIO1 and
GND to an external low-pass filter and AC-coupled amplifier.

Release `.bin` assets are encrypted [aes-gw2](https://github.com/fsedano/aes-gw2)
OTA containers, not raw ESP-IDF flash images. Application board ID: `hid.mbus485.pwm`;
recovery board ID: `BL-hid.mbus485.pwm`. Releases also include a matching host simulator.

The initial version is a bench prerelease; hardware waveform/load testing is
pending. The analog sweep runs without a gateway connection. Runtime analog
amplitude commands and a stream-loss timeout are not implemented yet.

The host simulator prints the current commanded amplitude to stdout while
running the same five-second up/down bench sweep. Its release asset is built
for the publishing machine’s operating system and architecture.
