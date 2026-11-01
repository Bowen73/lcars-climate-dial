# Home Assistant heating fork

This branch preserves the firmware used with a Home Assistant heating schedule.
The original project's licence, artwork and attribution remain in place.

## Dial behaviour

- Uses the thermostat's reported HVAC action for HEATING and IDLE.
- Pressing the dial toggles `input_boolean.lcars_schedule_enabled`.
- Schedule OFF keeps the thermostat in Heat at 7 degrees C for frost protection.
- The quiet screen says SCHEDULE OFF / FROST ONLY 7 degrees C.
- Turning the dial while scheduling is disabled only wakes the frost display.
- In normal operation the full LCARS display dims to 30 percent after one minute.
- Interaction or a new heating demand restores full brightness for one minute.
- Manual temperature changes hold until the next scheduled change.

## Home Assistant configuration

The household-specific Home Assistant package is kept locally and is not
published in this branch. Configure the schedule helper and thermostat handling
in Home Assistant before using this firmware. The helper must be called
`input_boolean.lcars_schedule_enabled`, and disabling it must retain frost
protection rather than disabling the physical thermostat.

The boiler watchdog and relay configuration are installation-specific and are
not included here. Keep the existing watchdog and relay interlocks in place.

## Building

The latest deployed firmware was compiled with ESPHome 2026.7.3. The optional
`firmware/local-lcars.yaml` wrapper uses `LCARS_BUILD_DIR` for a short Windows
temporary build path. Wi-Fi and API credentials are provisioned on the device;
they are not stored in this repository.

Upstream base: tag 1.1.0 (`f1b072e049c96a5155098c9ceb2dc0897bd586a8`).
Local firmware milestone: `c64cedd`.

