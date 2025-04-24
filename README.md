# Український голосовий пакет GLaDOS для робота пилосмока  
[![Банер](https://github.com/sverdlyuk/glados_ukr/blob/main/banner.png)](https://fpv-drones.sitepulse.com.ua)
[![Discord](https://img.shields.io/badge/Discord-Join-blue?logo=discord&style=flat-square)](https://discord.com/invite/kDv3hmpKbg)
[![YouTube](https://img.shields.io/badge/YouTube-Subscribe-red?style=flat-square&logo=youtube&logoColor=white)](https://www.youtube.com/@Lost_HumanVO)
[![DOU Blog](https://img.shields.io/badge/DOU-Blog-blue?style=flat-square&logo=readme&logoColor=white)](https://dou.ua/users/bogdan-sverdlyuk/articles/)

Цей голосовий пакет дозволяє вашому роботу-пилососу озвучувати свої дії голосом GLaDOS — штучного інтелекту з гри Portal 2, відомого своєю токсичністю, зверхністю та саркастичним гумором.
Проєкт створено за [фінансової підтримки ](https://dou.ua/forums/topic/50353/) української спільноти та озвучений неперевершеною Azla. Якщо ви не грали Portal та [Portal 2](https://youtu.be/0tkvdVWZKE0) у озвучці Lost Human, наполегливо рекомендую. Якщо вам потрібна якісна озвучка від Lost Human звертайтесь за адресою chernobyl6@gmail.com. 



[![Watch the video](https://img.youtube.com/vi/Gk78p5PVVB8/0.jpg)](https://youtu.be/Gk78p5PVVB8)



## 🚀Особливості
* Повна українська переозвучка: у пакеті для Dreame (tar.gz) переозвучені 199 оригінальних фраз робота.

* Фрази переписані з урахуванням чорного гумору та токсичної природи GLaDOS без втрати оригінального сенсу

* tar.gz пакет підходить для роботів пилососів Dreame, якщо є можливість завантаження голосового пакету у [специфікації](https://home.miot-spec.com) робота пилосмока
  
* .pkg пакет працює з Roborock першого та другого поколінь v1, M1S, S4, S5, S5e, S6, S6_MaxV, S6_Pure, T6  (пакет в процесі створення)



| url  | https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz |
|------|-------------------------------------------------------------------------------------|
| md5  | 3545e91c0626beccbd284469f6283a77                                                    |
| size | 9620968                                                                             |
| <a href="https://github.com/sverdlyuk/glados_ukr/raw/main/glados_samples.mp3" class="button" target="_blank">▶️ </a>  | [Завантажити приклад озвучення](https://github.com/sverdlyuk/glados_ukr/raw/main/glados_samples.mp3)|

## ⚙️Встановлення голосового пакету Dreame

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

## 🎙️ Як створити власний голосовий пакет Dreame
- Підготуйте файли `.ogg`, 16 000 Гц, Stereo/Mono відповідно до [таблиці фраз](https://github.com/oleksandr-belei/dreame-vacuum-uk-voice-packs/blob/main/ua_voice_mapping.csv). Можна створити лише 5-10 найпопулярніших фраз. Інші фрази будуть взяті з пакету-донора.
  
- Завантажте будь який існуючий голосовий пакет: [GLaDOS_ukr](https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz), [uk_female_pensive](https://github.com/oleksandr-belei/dreame-vacuum-uk-voice-packs/raw/refs/heads/main/voice_packs/uk_female_pensive), [dreame_female_uk](https://awsde0.fds.api.xiaomi.com/dreame-product/resources/59bcaf5201f15950c12917d0bb505321), [Лесь Подерев'янський](https://github.com/KonstantinDev7/Voice_Packs_for_Mi_Robot_S10_Plus/raw/refs/heads/main/Voice_Packs/LesV1ogg.tar.gz). Голосовий пакет це архів `tar.gz`. До прикладу голосовий пакет GLaDOS_ukr має розширення .gz Щоб відкрити архів замініть розширення з `.tar` на `tar.gz`. Аналогічно можна додати розширення пакету, що не має розширення. Відкрийте архів (у MacOS я використовував BetterZip) та замініть файли архіву своїми. Увага у архіві мають бути лише файли, а не папка з файлами.
  
- Завантажте голосовий пакет кудись онлайн, щоб отримати посилання на файл. Наприклад в публічний репозиторій GitHub, GitLab, FTP сервер тощо. Дізнайтесь розмір файлу у байтах та md5 суму файлу. Якщо не знаєте як це зробити можна скористатись онлайн сервісами.

## ⚙️Встановлення голосового пакету Midea M7 Pro
* Завантажте на свій ПК [SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools) та розпакуйте у будь-яку зручну теку. 
* Під'єднайте робота до ПК. USB порт знаходиться під верхньою кришкою під кнопкою Reset, він буде схований за заглушкою. 
* Запустіть командний рядок у розпакованій теці Platform Tools (ПКМ -> Відкрити в Terminal) та виконайте команду  ```adb devices```  щоб переконатися, що ваш пристрій розпізнається. Якщо є id вашого девайсу - все добре, якщо немає, то можливо ваш кабель не підходить для передачі інформації (я перепробував декілька з тих, що мав і лиш один з них підійшов). 
* Після цього завантажте [голосовий пак](https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/GLaDOS%20Midea.zip) та розпакуйте у будь-яку зручну для вас теку. Або ж ви можете завантажити власні файли, однак вони мають бути у форматі mp3 з частотою 64 kb/s mono 48000Hz. 
* Створіть текстовий файл у теці Platform Tools з наступним кодом:
```
@echo off
set SOURCE_FOLDER=повний шлях до теки зі звуками
for /r "%SOURCE_FOLDER%" %%x in (*) do (
    set "file=%%x"
    setlocal enabledelayedexpansion
    set "path=!file:%SOURCE_FOLDER%\=!"
    adb push "%%x" "/oem/sound/!path!"
    endlocal
)
```
* Змініть формат файлу з txt на bat, після чого виконайте його. 
* Готово!

## ⚙️Встановлення голосового пакету Roborock
Цей голосовий пакет має працювати на роботах пилососмоках Roborock 1 та 2 покоління (v1, M1S, S4, S5, S5e, S6, S6_MaxV, S6_Pure, T6). Я тестував на v1 (rockrobo.vacuum.v1, те саме що Gen 1 Xiaomi Mi SDJQRO2RR). Пилососи третього покоління мають голосові пакети підписані сертифікатом Roborock. Через це встановлення користувацьких голосових пакетів неможливе.
Щоб встановити голосовий пакет:
1. Завантажте [roborock_glados.pkg]([url](https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/roborock_glados.pkg)) на свій комп'ютер;
2. Встановіть [python-miio]([url](https://github.com/rytilahti/python-miio));
3. У командному рядку в теці з roborock_glados.pkg виконайте команду
```python
mirobo --ip 192.168.0.124 --token 50597y49p1894f6d6e67477349747408 install-sound roborock_glados.pkg
```
де `192.168.0.124` замініть на ip адресу свого робота пилосмока, а `50597y49p1894f6d6e67477349747408` на токен вашого робота пилосмока. Токен можна дізнатись за допомогою команди `python -m miio.cli cloud list` (Windows), `miiocli cloud list` (Linux, MacOS) або [будь якого іншого]([url](https://github.com/PiotrMachowski/Xiaomi-cloud-tokens-extractor)) зручного для вас методу.

## 🎙️ Як створити власний голосовий пакет Roborock
[Демо відео](https://www.youtube.com/shorts/RhcbOiGvVik?feature=share). Для створення власного голосового пакету потрібно:
1. Cтворити або завантажити файли в форматі .wav, бітрейт - 1411,2 КБ/с, частота дискретизації 44,1 кГц або 16,0 кГц;
2. Завантажити утиліту для шифрування [ccrypt]([url](https://ccrypt.sourceforge.net));
3. В командному рядку в теці з файлами виконати команду `tar zc *.wav | ccrypt -e -K "r0ckrobo#23456" > roborock_glados.pkg` де `roborock_glados.pkg` замінити на довільну назву свого голосового пакету.
4. Готово! Створений .pkg файл можна завантажувати на робот пилосмок.

## 👏 Подяки
Окрема подяка за просто титанічну роботу у створені цього голосового пакету [Lost Human](https://www.youtube.com/channel/UCZuVCATSHsgvBZMH-k3Gjcg) \
Дякую кожному хто фінансово підтримав цей проєкт. Без ваших пожертв він був би неможливий. Дякую [Oleksandr Belei](https://github.com/oleksandr-belei/dreame-vacuum-uk-voice-packs) за файл фраз Dreame, що був використаний у цьому проекті.
  
## 💬 Підтримка
Якщо щось залишилось незрозумілим або виникли труднощі з налаштуванням — не соромтесь звертатися за допомогою. Ви можете створити тему у [вкладці Discussions](https://github.com/sverdlyuk/glados_ukr/discussions), написати в чат [Розумний Будинок | Matrix](https://app.element.io/#/room/#selfhostedua:matrix.org), або залишити коментар до відповідного [топіку на DOU](https://dou.ua/forums/topic/49563/).

🔧 Якщо ви помітили неточності чи маєте ідеї для покращення — буду щиро вдячний за ваш pull request або відгук.

## 📜Ліцензія
Цей проєкт є відкритим і доступним за умовами ліцензії MIT. Ви можете вільно використовувати та змінювати його відповідно до умов ліцензії.
