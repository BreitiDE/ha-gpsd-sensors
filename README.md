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

By default, the integration looks for gpsd on `localhost` on port `2947`. If your
`gpsd` server is on a different host, you must configure the the `host` and `port`:

```yaml
sensor:
  - platform: gpsd_sensors
    name: GPSd Sensors
    host: gpsdhost.example.com
    port: 2947
```

If you want individual data as sensors, you can get the data from the attributes
array of the sensor. Add this to your template.yaml

```yaml
- sensor:
  - name: "GPS Latitude"
    unique_id: sensor.gps_latitude
    unit_of_measurement: "°"
    state: "{{ state_attr('sensor.gpsd_sensors', 'latitude') | round(7) }}"

- sensor:
  - name: "GPS Longitude"
    unique_id: sensor.gps_longitude
    unit_of_measurement: "°"
    state: "{{ state_attr('sensor.gpsd_sensors', 'longitude') | round(7) }}"

- sensor:
  - name: "GPS Elevation"
    unique_id: sensor.gps_elevation
    unit_of_measurement: "m"
    state: "{{ state_attr('sensor.gpsd_sensors', 'elevation') | round(0) }}"

- sensor:
  - name: "GPS Speed"
    unique_id: sensor.gps_speed
    unit_of_measurement: "km/h"
    state: "{{ state_attr('sensor.gpsd_sensors', 'speed') | round(0) }}"

- sensor:
  - name: "GPS Climb"
    unique_id: sensor.gps_climb
    unit_of_measurement: "m/min"
    state: "{{ state_attr('sensor.gpsd_sensors', 'climb') | round(0) }}"

- sensor:
  - name: "GPS Mode"
    unique_id: sensor.gps_mode
    state: "{{ state_attr('sensor.gpsd_sensors', 'mode') }}"
```


Thanks to zorrobyte <https://github.com/zorrobyte> and Djelibeybi <https://github.com/Djelibeybi> for their excellent work on the code, which I have adapted.

***

[HACS]: https://hacs.xys
