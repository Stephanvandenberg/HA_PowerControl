# HA_PowerControl

The following package, together with the Python script "update_entities.py," aims to prevent power disconnections due to excessive energy consumption from various household appliances (loads).

A fundamental hardware requirement is the presence of switches on the loads to be controlled and a sensor that measures the power consumption of each load.

I have used **Shelly 1PM** and **Shelly Plug S** devices, which are perfect for this purpose. It is recommended, though not mandatory, to use a sensor that monitors the total energy consumption of the installation (e.g., **Shelly EM** or an **ESP8266+PZEM**).

The logic is based on configuring two maximum power thresholds and two intervention timings (which reflect the operating logic of electricity meters used in Italy):

- If the total power consumption exceeds the "Delayed Maximum Power" value, the package waits for the number of minutes set in "Delayed Disconnection Minutes," after which it starts disconnecting loads;
- If the total power consumption exceeds the "Immediate Maximum Power" value, the system starts disconnecting loads immediately.

The disconnection order is defined using a list of priorities. The loads are reconnected when the power returns below the threshold. There are separate reconnection priorities, so you can decide whether to restore loads in the same or different order.

You can create your own reconnection logic by modifying the automation or using different load reconnection strategies.

**Note:** You must adapt entity names to match your installation!

## Compatibility

Tested with Home Assistant Core and supported by YAML automations and scripts. Compatible with Shelly devices and other smart switches/sensors capable of power monitoring.

## Installation

1. Copy the `packages/pc.yaml` file into your Home Assistant configuration.
2. Copy the Python script(s) in `python_scripts/` into your `python_scripts` folder.
3. Ensure that `python_script:` is enabled in your configuration.
4. Customize the YAML file with your entity IDs and power thresholds.
5. Reload automations and scripts or restart Home Assistant.

## Contribution

Feel free to open issues or pull requests. Feedback is welcome!

---

Created by an Italian Home Assistant enthusiast who loves power automation. 🇮🇹⚡
