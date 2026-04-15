# GPSd Sensors for Home Assistant

This component will set up a `sensor` platform that contains the current location,
altitude, speed, climb and time data from an external `gpsd` daemon.

## Installation

1. Add <https://github.com/Djelibeybi/ha-gpsd-sensors> as a custom `integration`
   repository in [HACS][HACS].
2. Add at least the following to `configuration.yaml` :

```yaml
sensor:
  - platform: gpsd_sensors
    name: GPSd Sensors
```

By default, the integration looks for GPSD on `localhost` on port `2947`. If your
`gpsd` server is on a different host, you must configure the the `host` and `port`:

```yaml
sensor:
  - platform: gpsd_sensors
    name: GPSd Sensors
    host: gpsdhost.example.com
    port: 2947
```

Thanks to 

***

[HACS]: https://hacs.xys
