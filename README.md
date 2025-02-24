> [!CAUTION]
> THIS MODULE HAS NOT BEEN TESTED, SO I DO NOT RECOMMEND USING IT, IF YOU
> INSTALL IT YOU DO IT AT YOUR OWN RISK !!!!

# Cirque Adapter
This module allows you to configure the drivers for your keyboard divided in the slave part.

Compatible with all boards with pro micro like the Nice!Nano, Puchi-Ble, clones and others.

Shields supported:
- cirque_adapter_left
- cirque_adapter_right

# Usage

- **Example for the left Shield:**
  ```bash
  west build -b nice_nano_v2 -- -DSHIELD="corne_left cirque_adapter_left"
  ```

- **Example for the right Shield:**
  ```bash
  west build -b nice_nano_v2 -- -DSHIELD="corne_right cirque_adapter_right"
  ```

# Configuration
Enable the drivers in the config file:

```conf
CONFIG_INPUT_PINNACLE=y
```

To use this module, first add it to your `config/west.yml` by adding a new
entry to `remotes` and `projects`:

```yaml
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: petejohanson # <-- enable the drivers
      url-base: https://github.com/petejohanson
    - name: mctechnology17 # <-- enable this module
      url-base: https://github.com/mctechnology17
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    - name: cirque-input-module # <-- enable the drivers
      remote: petejohanson
      revision: main
    - name: zmk-cirque-adapter # <-- enable this module
      remote: mctechnology17
      revision: main
  self:
    path: config
```

Now simply indicate in the board and the shield in the `build.yaml` file:

```yaml
---
include:
  - board: nice_nano_v2
    shield: corne_left cirque_adapter_left
  - board: nice_nano_v2
    shield: corne_right cirque_adapter_right
```

[//]: # ( vim: set fdm=marker: )
