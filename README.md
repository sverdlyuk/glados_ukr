# GLaDOS голосовий пакет для робота пилососа 

## 💡Вступ
Цей голосовий пакет дозволяє вашому роботу-пилососу озвучувати свої дії голосом GLaDOS — штучного інтелекту з гри Portal 2, відомого своєю токсичністю та саркастичним гумором.
Проєкт створено за фінансової підтримки української спільноти та озвучений Azla з студії [Lost Human](https://www.youtube.com/channel/UCZuVCATSHsgvBZMH-k3Gjcg), яка брала участь в озвучуванні Portal 2. Якщо ви ніколи не грали Portal це чудова нагода.

## 🚀Особливості
Повна переозвучка: у пакеті переозвучені всі 199 оригінальних фраз робота. \
Оновлений контент: більшість фраз переписані з урахуванням чорного гумору та токсичної природи GLaDOS. \
Усі репліки переписані так, щоб не втрачався сенс оригіналу \
Підходить для роботів пилососів Dreame, Mijia та Mova якщо є можливість завантаження у [специфікації](https://home.miot-spec.com) робота пилосмока

| Голосовий пакет                                     | Опис                                | md5                            | Розмір           | Samples                                             |
|-----------------------------------------------|--------------------------------------------|---------------------------------|----------------|-----------------------------------------------------------|
| [uk_female_pensive](voice_packs/uk_female_pensive/) | *Pensive, introspective, soft, and lovely* | `55bfe4272ce1e77d9bbafebf9ec99330` | `3585448` | <p align="center">[🔗](voice_samples/uk_female_pensive)</p> |

## ⚙️Встановлення

You can install the Ukrainian voice pack on your Dreame vacuum cleaner using one of the following methods:

### 1. Installing on Official Firmware with [Home Assistant](https://www.home-assistant.io/)
- Install the custom [Dreame vacuum](https://github.com/Tasshack/dreame-vacuum.git)  integration for Home Assistant, created by **@Tasshack**.
- In Home Assistant, navigate to `"Developer Tools"` -> `"Services"` and switch to `YAML mode`.
- Paste the following code:

  ```yaml
  service: dreame_vacuum.vacuum_install_voice_pack
  data:
    lang_id: UK
    url: Raw URL for the voice pack from the "voice_packs" directory in this repository.
    md5: The hash of the voice pack.
    size: The file size of the voice pack in bytes.
  target:
    entity_id: vacuum.dreame
  ```
- Call the service to set the new voice pack.

### 2. Installing on Custom Firmware with [Valetudo](https://valetudo.cloud/)
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
