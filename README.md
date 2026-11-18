> [!CAUTION]
> THIS MODULE HAS NOT BEEN TESTED, SO I DO NOT RECOMMEND USING IT, IF YOU
> INSTALL IT YOU DO IT AT YOUR OWN RISK !!!!

# Cirque Adapter
This module allows you to configure the drivers for your keyboard divided in the slave part.

Compatible with all boards with pro micro like the Nice!Nano, Puchi-Ble, clones and others.

Shields supported:
- cirque_adapter_left
- cirque_adapter_right

# Versions, branches and tags

All my ZMK projects follow the same rules. The idea is that every project can be paired with ZMK in its different versions (v0.3, v0.4, ...), so you always know which branch or tag fits the ZMK version you use.

What to write as `revision:` in your `west.yml`:

| You want | `revision:` |
|---|---|
| The latest stable version | `main` |
| Stay on ZMK v0.3 | `zmk-v0.3` |
| A fixed version that never changes | a tag, for example `v0.0.3` |

Branches:

- `main`: the stable version. It follows the newest ZMK version that the project supports. Today that is ZMK v0.3.
- `zmk-v0.3`: the line for ZMK v0.3. While `main` is on ZMK v0.3 both are the same. When `main` moves to a newer ZMK, this branch stays on ZMK v0.3 and keeps receiving fixes. The next lines are created the same way (`zmk-v0.4`, ...).
- `dev`: development. It can be broken at any time, do not use it for your keyboard.

Tags:

The third number of a tag is the ZMK version it is made for:

- `v0.0.3`: the common starting point of all my ZMK projects (Nov 18, 2026), for ZMK v0.3.
- `v0.0.3.1`, `v0.0.3.2`, ...: the next versions for ZMK v0.3, new features and fixes.
- `v0.0.4`, `v0.0.4.1`, ...: the versions for the next ZMK version (v0.4).
- A version that is still being tested carries a suffix, for example `v0.0.3.1-fix`.

Every release says which ZMK version it was tested with. The full list of changes is in [CHANGELOG.txt](CHANGELOG.txt).

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
