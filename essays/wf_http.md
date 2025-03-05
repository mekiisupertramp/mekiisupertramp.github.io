---
layout: essay
type: essay
title: "WallFrame 2/6 - HTTP [in progress..]"
image: img/wf_rgb/wf_logo.png
# All dates must be YYYY-MM-DD format!
date: 2025-01-05
published: true
labels:
  - Raspberry Pi  Pico WH
  - Python
  - WS2812B
---

# Introduction
This guide will walk you through the process of setting up Visual Studio Code (VS Code) for programming the Raspberry Pi Pico W using the MicroPico module, and then driving RGB LEDs (e.g. WS2812B). The Raspberry Pi Pico W is a microcontroller board with built-in Wi-Fi capabilities, and the MicroPico module allows you to program it using MicroPython.
# HTTP Server for RGB LED Control

## Introduction
This documentation explains how to set up an HTTP server on a Raspberry Pi Pico WH to control RGB LED strips. The `main.py` script demonstrates the initialization of the HTTP server, handling client connections, and processing HTTP requests to control the LEDs.

## Hardware Requirements
- Raspberry Pi Pico WH
- RGB LED strips
- Breadboard
- Jumper wires
- Power supply

## Software Requirements
- MicroPython
- Thonny IDE (or any other MicroPython-compatible IDE)

## Setting Up the Hardware
### Connecting the RGB LED Strips
1. Connect the DIN (Data In) pin of the LED strip to a specific GPIO pin on the Pico WH.
2. Connect the GND (Ground) pin of the LED strip to the GND pin on the Pico WH.
3. Connect the VCC (Voltage) pin of the LED strip to the 5V power supply.

### Power Supply
Ensure the power supply is adequate for the number of LEDs you are using.

## Setting Up the Software
### Installing MicroPython
1. Download the MicroPython firmware for the Pico WH.
2. Use a tool like `mpfshell` or the Thonny IDE to upload the firmware to the Pico WH.

### Connecting to the Pico WH
1. Connect to the Pico WH via USB for programming.
2. Open a serial connection and upload scripts.

## Setting Up the HTTP Server
### WLAN Configuration
```python
import network    
import time
import socket
import neopixel

ssid = '##########'
password = '##########'

# Define the static IP address for the Raspberry Pi Pico WH
static_ip = '192.168.1.20'
# Define the subnet mask for the network
subnet_mask = '255.255.255.0'
# Define the gateway IP address, usually the IP of your router
gateway = '192.168.1.1'
# Define the DNS server IP address, using Google's DNS in this case
dns_server = '8.8.8.8'


# Initialize the Wi-Fi interface in station mode
wlan = network.WLAN(network.STA_IF)
# Activate the Wi-Fi interface
wlan.active(True)
# Set the hostname for the device
wlan.config(hostname="MyPicoW-1")
# Configure the Wi-Fi interface with the static IP, subnet mask, gateway, and DNS server
wlan.ifconfig((static_ip, subnet_mask, gateway, dns_server))
# Connect to the Wi-Fi network using the provided SSID and password
wlan.connect(ssid, password)

```
### Connection test
```python
# Set the maximum wait time for the Wi-Fi connection attempt
max_wait = 10

# Loop until the maximum wait time is reached
while max_wait > 0:
    # Check the Wi-Fi connection status
    if wlan.status() >= 3:  # 3 indicates a successful connection
        print('Connected to Wi-Fi')
        print('IP Address:', wlan.ifconfig()[0])
        break # breaks the loop!
    max_wait -= 1
    print('Waiting for connection...')
    # Wait for 1 second before the next attempt
    time.sleep(1)
```

# Demonstration
