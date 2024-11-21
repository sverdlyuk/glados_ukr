# Український голосовий пакет GLaDOS для робота пилосмока  
[![Банер](https://github.com/sverdlyuk/glados_ukr/blob/main/banner.png)](https://fpv-drones.sitepulse.com.ua)

## 💡Вступ
Цей голосовий пакет дозволяє вашому роботу-пилососу озвучувати свої дії голосом GLaDOS — штучного інтелекту з гри Portal 2, відомого своєю токсичністю та саркастичним гумором.
Проєкт створено за [фінансової підтримки української спільноти](https://dou.ua/forums/topic/50353/) та озвучений Azla з студії [Lost Human](https://www.youtube.com/channel/UCZuVCATSHsgvBZMH-k3Gjcg), які озвучили Portal 2. Якщо ви ніколи не грали Portal це чудова нагода.



[![Watch the video](https://img.youtube.com/vi/Gk78p5PVVB8/0.jpg)](https://youtu.be/Gk78p5PVVB8)

[![Discord](https://img.shields.io/badge/Discord-Join-blue?logo=discord&style=flat-square)](https://discord.com/invite/kDv3hmpKbg)

## 🚀Особливості
* Повна українська переозвучка: у пакеті для Dreame (tar.gz) переозвучені 199 оригінальних фраз робота.

* Фрази переписані з урахуванням чорного гумору та токсичної природи GLaDOS без втрати оригінального сенсу

* tar.gz пакет підходить для роботів пилососів Dreame, Mijia та Mova якщо є можливість завантаження голосового пакету у [специфікації](https://home.miot-spec.com) робота пилосмока
  
* .pkg пакет працює з Roborock v1, v2, v3: S5, S6, T6, S7, S8, Q7, S50, S51, S55 та іншими (пакет в процесі створення)



| url  | https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz |
|------|-------------------------------------------------------------------------------------|
| md5  | 3545e91c0626beccbd284469f6283a77                                                    |
| size | 9620968                                                                             |
| <a href="https://github.com/sverdlyuk/glados_ukr/raw/main/glados_samples.mp3" class="button" target="_blank">▶️ </a>  | [Завантажити приклад озвучення](https://github.com/sverdlyuk/glados_ukr/raw/main/glados_samples.mp3)|

## ⚙️Встановлення

Ви можете встановити голосовий пакет GLaDOS декількома способами. Детальну інструкцію можна переглянути [тут](https://dou.ua/forums/topic/49563/).

### 1. Home Assistant інтеграція Dreame Vacuum
- Встановіть інтеграцію [Dreame vacuum](https://github.com/Tasshack/dreame-vacuum.git). 
  
[![Add to HACS via My Home Assistant](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=Tasshack&repository=dreame-vacuum&category=integration)

- В Home Assistant, перейдіть до `"Інструменти для розробників"` -> `"Дії"` та переключіться в `YAML mode`
- Вставте наступний код:

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

- Замініть entity_id `vacuum.mops` на entity_id вашого робота пилосмока
- Натисніть кнопку Виконати Дію.

### 2. Home Assistant інтеграція Xiaomi Miot
- Встановіть інтеграцію [Xiaomi Miot Auto](https://github.com/al-one/hass-xiaomi-miot)

[![Add to HACS via My Home Assistant](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=al-one&repository=hass-xiaomi-miot&category=integration)

- В Home Assistant, перейдіть до `"Інструменти для розробників"` -> `"Дії"` та переключіться в `YAML mode`
- Вставте наступний код:

 ```yaml
service: xiaomi_miot.set_miot_property
data:
  entity_id: vacuum.dreame_p2041o_796c_robot_cleaner
  siid: 7 # siid для аудіосервісу
  piid: 4 # piid для встановлення голосового пакету
  value: '{"id":"UK","url":"https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz","md5":"3545e91c0626beccbd284469f6283a77","size":9620968}'
  ```
- Замініть entity_id `vacuum.dreame_p2041o_796c_robot_cleaner` на entity_id вашого робота пилосмока
  
### 3. Python Miio (genericmiot)
- Встановіть Python Miio
- Запустіть команду
```python
python -m miio.cli genericmiot --ip 192.168.50.157 --token 614a498f6c72506d6e3066764f73696a raw_command set_properties "[{'did': '8023334994', 'siid': 7, 'piid': 4, 'value' : '{\"id\":\"UK\",\"url\":\"https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz\",\"md5\":\"3545e91c0626beccbd284469f6283a77\",\"size\":9620968}'}]"
```

### 4. Python Miio (device)
```python
miiocli device --ip 192.168.50.157 --token 614a498f6c72506d6e3066764f73696a raw_command set_properties "[{'did': '8023334994', 'siid': 7, 'piid': 4, 'value' : '{\"id\":\"UK\",\"url\":\"https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz\",\"md5\":\"3545e91c0626beccbd284469f6283a77\",\"size\":9620968}'}]"
```
- Змініть IP та token на власні

  
### 5. Valetudo
- Відкрийте веб-інтерфейс Valetudo, ввівши IP-адресу вашого пилососа у веб-браузері.
- У Valetudo, перейдіть до `"Robot Settings"`-> `"Misc Settings."`
- Вставте наступні параметри в секцію `"Voice packs"`:
    - URL: https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz
    - Language Code: 'UK'
    - Hash: 3545e91c0626beccbd284469f6283a77
    - File size: 9620968
- Збережіть та натисніть `"Set Voice Pack`."


## 📜Ліцензія
Цей проєкт є відкритим і доступним за умовами ліцензії MIT. Ви можете вільно використовувати та змінювати його відповідно до умов ліцензії.

## 💬Оговорення
Якщо у вас є запитання, пропозиції чи відгуки, відвідайте [вкладку Discussions](https://github.com/sverdlyuk/glados_ukr/discussions) цього репозиторію. Не соромтеся розпочинати нові обговорення або долучатися до існуючих. Також можете поставити своє питанння в коментарях у [топіку на DOU](https://dou.ua/forums/topic/49563/).
