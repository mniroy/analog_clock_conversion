# Analog Clock Conversion with ESPHome

This project converts a quartz analog clock to be controlled by an ESP D1 Mini (ESP8266) using ESPHome.

## Requirements

- ESP D1 Mini (ESP8266)
- Quartz analog clock
- ESPHome installed
- Home Assistant (optional, for integration)
- Jumper wires
- Soldering tools (optional, for permanent connections)

## Hardware Setup

1. **Disassemble the Quartz Clock**:
   - Carefully open the quartz clock to access the internal clock coil.
   - Identify the two terminals of the clock coil.

2. **Connect the ESP D1 Mini**:
   - Connect one terminal of the clock coil to GPIO pin D1 on the ESP D1 Mini.
   - Connect the other terminal of the clock coil to GPIO pin D2 on the ESP D1 Mini.
   - Ensure the connections are secure. You can use jumper wires or solder the connections for a more permanent setup.

3. **Power the ESP D1 Mini**:
   - Connect the ESP D1 Mini to a power source (e.g., USB power adapter or battery pack).

## Configuration

1. **Clone the repository**:
   ```sh
   git clone https://github.com/mniroy/analog_clock_conversion.git
   cd analog_clock_conversion
   ```

2. **Edit the `analog_clock.yaml` file**:
   - Update the WiFi credentials:
     ```yaml
     wifi:
       ssid: "your_SSID"
       password: "your_PASSWORD"
     ```
   - Update the API and OTA passwords:
     ```yaml
     api:
       password: "api_password"
     ota:
       password: "ota_password"
     ```

3. **Upload the configuration to the ESP D1 Mini**:
   ```sh
   esphome run analog_clock.yaml
   ```

## Operating the Clock

### Adjusting Clock Speed

The clock speed can be adjusted using the web server endpoints:

- **Increase speed**: Access `http://<ESP_IP>/speed_up`
- **Decrease speed**: Access `http://<ESP_IP>/slow_down`

Replace `<ESP_IP>` with the IP address of your ESP D1 Mini.

### Accessing the Web Server

1. Connect your device to the same network as the ESP D1 Mini.
2. Open a web browser and enter the IP address of the ESP D1 Mini.
3. Use the provided endpoints to adjust the clock speed:
   - `http://<ESP_IP>/speed_up` to increase the speed.
   - `http://<ESP_IP>/slow_down` to decrease the speed.

### Home Assistant Integration

If you are using Home Assistant, the ESP D1 Mini will automatically integrate with it. You can control and monitor the clock from the Home Assistant interface.

## Troubleshooting

- Ensure the ESP D1 Mini is connected to the correct WiFi network.
- Check the logs for any errors:
  ```sh
  esphome logs analog_clock.yaml
  ```

## License

This project is licensed under the MIT License.