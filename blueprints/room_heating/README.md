# Room heating

[![Import blueprint into Home Assistant](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ftenjaa%2Fhome-assistant-blueprints%2Fblob%2Fmain%2Fblueprints%2Froom_heating%2Froom_heating.yaml)

**One room. Two helpers. Everything else is autodetected.**
TRVs, windows, and temperature sensors: no individual entity lists.

_Inspired by [Advanced Heating Control](https://github.com/panhans/HomeAssistant/blob/main/blueprints/automation/panhans/advanced_heating_control.yaml) by panhans._

## Features

### Autodetection of entities

The automation automatically detects all TRVs, window contacts, and temperature sensors in the room.
Select the room and the two required helpers; no individual entity lists are needed.

### Comfort, away, and night temperatures

The automation supports three different temperature settings: comfort, away, and night.

- comfort temperature: home is occupied and night mode is off
- away temperature: home is unoccupied, regardless of night mode
- night temperature: home is occupied and night mode is on

### Offset calibration

The automation evaluates calibration when a usable external sensor reading or a thermostat's current temperature changes, on startup, and after automation reloads.
An updated offset is written at most every 10 minutes and only if the value differs by more than 0.5 °C.
Sensors belonging to thermostat devices are ignored by default.
You can exclude additional sensors from calibration by adding them to the `excluded_sensors` list in the automation.

The offset formula assumes an additive Celsius offset already included in the TRV reading.
Open windows pause calibration.

### Window detection

The automation turns off heating after a window has been open for 5 seconds and resumes heating once all windows have been closed for 5 seconds.

### Allows manual temperature and HVAC mode changes

Heating settings are applied on helper/window changes, Home Assistant startup, and automation reloads.
Manual temperature and HVAC mode changes are preserved until one of these events.
Temperature-change triggers and the 10-minute fallback change calibration offsets only; they do not reset setpoints or HVAC modes.

## Setup

You can install the blueprint via the installation button above.
Assign devices/entities to the room's Home Assistant area, then select the room, one Home Occupied helper, and one Night Mode helper.
Optionally adjust the comfort, away, and night temperatures.

For more information on the helpers, see the [base helpers](../../README.md#base-helpers) section in the main README.
