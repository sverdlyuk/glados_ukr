# Український голосовий пакет GLaDOS для робота пилосмока  

## 💡Вступ
Цей голосовий пакет дозволяє вашому роботу-пилососу озвучувати свої дії голосом GLaDOS — штучного інтелекту з гри Portal 2, відомого своєю токсичністю та саркастичним гумором.
Проєкт створено за фінансової підтримки української спільноти та озвучений Azla з студії [Lost Human](https://www.youtube.com/channel/UCZuVCATSHsgvBZMH-k3Gjcg), яка брала участь в озвучуванні Portal 2. Якщо ви ніколи не грали Portal це чудова нагода.

## 🚀Особливості
* Повна українська переозвучка: у пакеті переозвучені 199 оригінальних фраз робота.

* Фрази переписані з урахуванням чорного гумору та токсичної природи GLaDOS без втрати оригінального сенсу

* tar.gz пакет підходить для роботів пилососів Dreame, Mijia та Mova якщо є можливість завантаження голосового пакету у [специфікації](https://home.miot-spec.com) робота пилосмока
  
* .pkg пакет працює з Roborock v1 (Xiaomi Mijia v1), s5, s50... та іншими (пакет в процесі створення)



| url  | https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz |
|------|-------------------------------------------------------------------------------------|
| md5  | 3545e91c0626beccbd284469f6283a77                                                    |
| size | 9620968                                                                             |

## ⚙️Встановлення

Ви можете встановити голосовий пакет GLaDOS декількома способами

### 1.[Home Assistant](https://www.home-assistant.io/) інтеграція Dreame Vacuum
- Встановіть інтеграцію [Dreame vacuum](https://github.com/Tasshack/dreame-vacuum.git) 
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
  ``
- Замініть entity_id vacuum.mops на entity_id вашого робота пилосмока
- Натисніть кнопку Виконати Дію.

### 2.[Home Assistant](https://www.home-assistant.io/) інтеграція Xiaomi Miot
- Встановіть інтеграцію [Xiaomi Miot Auto](https://my.home-assistant.io/redirect/hacs_repository/?owner=al-one&repository=hass-xiaomi-miot)
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



### 3. Встановлення за допомогою [Valetudo](https://valetudo.cloud/)
- Open Valetudo's web interface by entering your vacuum's IP address in a web browser.
- In Valetudo, navigate to `"Robot Settings"`-> `"Misc Settings."`
- Enter the following information in the `"Voice packs"` section:
    - **URL:** Raw URL for the voice pack from the "voice_packs" directory in this repository.
    - **Language Code:** 'UK'
    - **Hash:** The hash of the voice pack.
    - **File size:** The file size of the voice pack in bytes.
- Save the settings by clicking `"Set Voice Pack`."

### 3. Installing on Official Firmware with [Python MIIO](https://python-miio.readthedocs.io/en/latest/)
Detailed installation instructions can be found in the [python-miio](https://github.com/rytilahti/python-miio.git) repository, created by **@rytilahti**.

## 📜Ліцензія
Цей проєкт є відкритим і доступним за умовами ліцензії MIT. Ви можете вільно використовувати та змінювати його відповідно до умов ліцензії.

## 💬Оговорення
Якщо у вас є запитання, пропозиції чи відгуки, відвідайте вкладку Обговорення цього репозиторію. Не соромтеся розпочинати нові обговорення або долучатися до існуючих. Також можете поставити своє питанння в коментарях у [топіку на DOU](https://dou.ua/forums/topic/49563/).
