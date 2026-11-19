<!-- mc-follow-top:start -->
<div align="center">

  <a href="https://youtube.com/@mctechnology17">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://github.com/mctechnology17/mctechnology17/blob/main/src/mctechnology_banner_dark.png?raw=true" />
      <img alt="MC Technology" width="420px" src="https://github.com/mctechnology17/mctechnology17/blob/main/src/mctechnology_banner_light.png?raw=true" />
    </picture>
  </a>
  <br>
  <a href="https://youtube.com/@mctechnology17"><img align="center" alt="MC Technology | YouTube" width="22px" src="https://github.com/mctechnology17/mctechnology17/blob/main/src/youtube.png" /></a>
  <a href="https://www.instagram.com/mctechnology17/"><img align="center" alt="MC Technology | Instagram" width="22px" src="https://github.com/mctechnology17/mctechnology17/blob/main/src/instagram.png" /></a>
  <a href="https://www.facebook.com/mctechnology17/"><img align="center" alt="MC Technology | Facebook" width="22px" src="https://github.com/mctechnology17/mctechnology17/blob/main/src/facebook.png" /></a>
  <a href="https://www.tiktok.com/@mctechnology17"><img align="center" alt="MC Technology | TikTok" width="22px" src="https://github.com/mctechnology17/mctechnology17/blob/main/src/tiktok.png" /></a>
  <a href="https://t.me/mctechnology17"><img align="center" alt="MC Technology | Telegram" width="22px" src="https://github.com/mctechnology17/mctechnology17/blob/main/src/telegram.png" /></a>
  <a href="https://discord.gg/7zs2fezBbv"><img align="center" alt="MC Technology | Discord" width="22px" src="https://github.com/mctechnology17/mctechnology17/blob/main/src/discord.png" /></a>

</div>
<!-- mc-follow-top:end -->

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

<!-- mc-follow:start -->
# Support this project

This is a personal project that I build in my free time. If it is useful to
you, the best way to help is to follow and subscribe:

[YouTube](https://youtube.com/@mctechnology17) · [Instagram](https://www.instagram.com/mctechnology17/) · [Facebook](https://www.facebook.com/mctechnology17/) · [TikTok](https://www.tiktok.com/@mctechnology17)

News and community: [Telegram](https://t.me/mctechnology17) · [Discord](https://discord.gg/7zs2fezBbv)

I make videos about split keyboards, ZMK and open source (in Spanish, long
videos with English subtitles). Every follow and every subscription helps me a
lot and keeps me motivated to bring more to the open source community.

Thank you for every report and every issue: they make these projects better.
<!-- mc-follow:end -->

[//]: # ( vim: set fdm=marker: )
