---
title: Shelly
description: Integrate Shelly devices
ha_category:
  - Cover
  - Light
  - Sensor
  - Switch
ha_release: 0.115
ha_codeowners:
  - '@balloob'
  - '@bieniu'
ha_iot_class: Local Polling
ha_domain: shelly
featured: true
ha_config_flow: true
---

Integrate [Shelly devices](https://shelly.cloud) into Home Assistant.

## Configuration

To add a Shelly device to your installation, make sure they are connected to your Wi-Fi network first. Next, go to **Configuration** >> **Integrations** in the UI. If the new device is on the same network as Home Assistant, it is discovered automatically. Clicking "Configure" on the discovered device, adds it to Home Assistant. If your device isn't discovered automatically, click the button with `+` sign on the integrations page and from the list of integrations, select **Shelly** and follow the instructions shown.

<div class="note">
Integration is communicating directly with the device; cloud connection is not needed.
</div>

## Entity naming

The integration uses the following strategy to name its entities:

- If `Device Name` or `Channel Name` is set in the device, the integration will use them to generate the entities' name.
- If channel names are set, they will be used in the entity names. The device name will not be used.
- If only the device name is set, and the device has multiple channels, the channel number will be appended to the entity name (e.g., Channel 2).
- In case device name and channel names are not set, the entity name will be generated by the `Device Type`, `Device ID` and `Channel Number`.

Examples:

| Device Name | Channel Name   | Entity Name                     |
| ----------- | -------------- | --------------------------------|
| `Not set`   |	`Not Set`	     | shellyswitch25-ABC123 Channel 1 |
| `Not set`	  | Kids Room Bulb | Kids Room Bulb                  |
| Kitchen     |	`Not Set`	     | Kitchen Channel 1               |
| Bedroom	    | Round Bulb     | Round Bulb                      |

Names are set from the device web page:

- Device name can be set in **Settings** >> **DEVICE NAME**
- Channel name for single-channel devices can be set in **Settings** >> **CHANNEL NAME**
- Channel name for multi-channel devices can be set in **Settings** >> **CHANNEL NAME** after selecting the channel, by clicking on the channel name.

## Known issues and limitations

- Only supports firmware 1.8 and later
- Support relays, lights (with brightness), sensors and rollers
- Support for battery-powered devices is currently very limited
