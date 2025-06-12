# Ukrainian GLaDOS Voice Pack for Robot Vacuum Cleaner
[![SWUbanner](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/banner-direct-single.svg)](https://stand-with-ukraine.pp.ua/)

[🇺🇦 Інструкція українською](https://github.com/sverdlyuk/glados_ukr/blob/main/README_ukr.md). This voice pack lets your robot vacuum speak using the voice of GLaDOS — the artificial intelligence from Portal 2, known for her sarcasm, superiority complex, and dark humor.  
The project was made possible with [financial support](https://dou.ua/forums/topic/50353/) from the Ukrainian community.

## 🚀Features

The phrases have been rewritten with GLaDOS's signature dark humor and toxic personality — without losing the original meaning.


| Brand     | Package Format | Supported Models                                                                                      |
|-----------|----------------|--------------------------------------------------------------------------------------------------------|
| Roborock  | .pkg           | First- and second-generation robots: v1, M1S, S4, S5, S5e, S6, S6 MaxV, S6 Pure, T6                    |
| Dreame    | tar.gz         | All `dreame.vacuum` models that support voice package installation via the [specification](https://home.miot-spec.com/s/dreame.vacuum)  |
| Xiaomi    | tar.gz         | All `xiaomi.vacuum` models that support voice package installation via the [specification](https://home.miot-spec.com/s/xiaomi.vacuum) |
| Midea     | .zip           | Midea M7 Pro                                                                                          |


## ⚙️Installing the Dreame Voice Pack

You can install the GLaDOS voice pack in several ways. A detailed guide is available [here](https://dou.ua/forums/topic/49563/).

| url  | https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz |
|------|-------------------------------------------------------------------------------------|
| md5  | 3545e91c0626beccbd284469f6283a77                                                    |
| size | 9620968                                                                             |
| <a href="https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/Other%20files/glados_samples.mp3" class="button" target="_blank">▶️ </a>  | [Download sample voice](https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/Other%20files/glados_samples.mp3)|

### 1. Home Assistant with Dreame Vacuum Integration
- Install the [Dreame vacuum](https://github.com/Tasshack/dreame-vacuum.git) integration.

[![Add to HACS via My Home Assistant](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=Tasshack&repository=dreame-vacuum&category=integration)

- In Home Assistant, go to `"Developer Tools"` -> `"Services"` and switch to `YAML mode`
- Paste the following code:

  ```yaml
  service: dreame_vacuum.vacuum_install_voice_pack
  data:
    lang_id: UK
    url: >-
      https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz
    md5: 3545e91c0626beccbd284469f6283a77
    size: 9620968
  target:
    entity_id: vacuum.mops
