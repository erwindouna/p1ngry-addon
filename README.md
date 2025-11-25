# Home Assistant p1nrgy add-on repository

p1nrgy is a Home Assistant add-on that reads energy consumption data from DSMR-compatible smart meters and publishes the data to an MQTT broker. It's aim is to be blazing fast and lightweight, ideal for running on resource-constrained devices like Raspberry Pi.

p1nrgy is written in Go, so it compiles to a single binary and not using an interpreter, making it very/more efficient in terms of CPU and memory usage.
The idea is also to keep it as simple as it gets, reader the DSMR data, parsing it, and publishing it to MQTT. It's then up to the user in Home Assistant to consume the MQTT data.

## Supported Architectures

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]

## Installation

In order to install this add-on, you need to add this repository to your Home Assistant instance. You can do this by clicking the badge below:

[![Open your Home Assistant instance and show the add add-on repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Ferwindouna%2Fp1ngry-addon)

## Configuration

By default, p1nrgy provides a basic configuration that should work for most DSMR smart meters using a serial connection. However, you may need to adjust the settings based on your specific setup. Available configuration options:

@Erwin: add the options per DSMR V3, V4, etc.

- `dsmr_enabled`: Enable or disable DSMR reading (default: true)
- `dsmr_mode`: Mode of DSMR connection, either "serial" or "tcp" (default: "serial")
- `dsmr_serial_device`: Serial device path for DSMR connection (default: "/dev/ttyUSB0")
- `dsmr_serial_baud`: Baud rate for serial connection (default: 115200)
- `dsmr_serial_databits`: Number of data bits for serial connection (default: 8)
- `dsmr_serial_parity`: Parity for serial connection, either "N", "E", or "O" (default: "N")
- `dsmr_serial_stopbits`: Number of stop bits for serial connection (default: 1)

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg
