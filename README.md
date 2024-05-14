# LM75A Temperature Sensor Component for ESPHome

<img src="device.png" width="300">

## How to install
### From Home Assistant Web Browser
```
Requirements:
- ESPHome addon installed
- File editor addon installed
- Downloaded ESPHome-LM75A-Temperature-Sensor-Component github repo
```
1) using ESPHome Create project: `my_project_name`

1) using File Editor addon, go to path `homeassistant/esphome/`

2) upload _LM75A.cpp_ file to the same folder as _my\_project\_name.yaml_.

4) upload _LM75A.h_ file to the same folder as _my\_project\_name.yaml_.


5) Edit _my_project.yaml_ file.

Add _includes_ subsection of _esphome_.
```
esphome:
  includes:
    - LM75A.h
    - LM75A.cpp
```
Add _I2C_ and _sensor_ sections to end of file.
```
i2c:
  - id: bus_a
    sda: 4
    scl: 5
    scan: True
sensor:    
  - platform: custom
    lambda: |-
     auto lm75a = new LM75A();
     App.register_component(lm75a);
     return {lm75a};
    sensors:
      name: "LM75A Temperature"
      unit_of_measurement: °C
      accuracy_decimals: 1
```

6) on the top left corner, click Install

7) enjoy


### ESPHome Command Line

1) Create project: `esphome my_project.yaml wizard`

2) Compile project: `esphome my_project.yaml compile` _(this creates a project src folder)_

3) Copy _LM75A.cpp_ file to the project _src_ folder.

4) Copy _LM75A.h_ file to the same folder as _my\_project.yaml_.

5) Edit _my_project.yaml_ file.

Add _includes_ subsection of _esphome_.
```
esphome:
  includes:
    - LM75A.h
```
Add _I2C_ and _sensor_ sections to end of file.
```
i2c:
  - id: bus_a
    sda: 4
    scl: 5
    scan: True
sensor:    
  - platform: custom
    lambda: |-
     auto lm75a = new LM75A();
     App.register_component(lm75a);
     return {lm75a};
    sensors:
      name: "LM75A Temperature"
      unit_of_measurement: °C
      accuracy_decimals: 1
```

6) Compile and upload project: `esphome my_project.yaml run`

## How to connect the sensor
<img src="schematics.png" width="400">

## License

This project is under MIT license. This means you can use it as you want (just don't delete the library header).

## Original Project ##

It is a modified <a target="_blank" href="https://github.com/QuentinCG/Arduino-LM75A-Temperature-Sensor-Library">Arduino-LM75A-Temperature-Sensor-Library</a> project by <a target="_blank" href="https://github.com/QuentinCG">QuentinCG</a>.
