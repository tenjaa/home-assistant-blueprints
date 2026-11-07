# Home Assistant blueprints

A collection of my Home Assistant automation blueprints.

## Blueprints

- [Room heating](blueprints/room_heating/): choose a room, a home-occupied helper,
  and a night mode helper. TRVs, window sensors, and temperature sensors are
  detected automatically. No individual entity lists to maintain.

## Base helpers

My home uses three shared `input_boolean` helpers as the basis for automations.
This has the advantage of being able to change the behavior of all automations at once by changing the automation to set the helper states.
The Home Occupied helper is flaky? Just improve the automation that sets it and all automations will benefit.

### Home Occupied

This is **On** when at least one person is home, and **Off** when nobody is home.

This can be easily set automatically by a presence detection automation or based on a device tracker.

### Night Mode

This is **On** when night mode or bedtime is active, and **Off** during normal daytime operation.

Night Mode can be easily activated by the good-night button by the bed and deactivated automatically a few minutes before the alarm.

### Vacation

This is **On** when away on vacation, and **Off** during normal operation.

This is set manually and distinguishes a longer trip from everyday absence.
