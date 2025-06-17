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

- Replace the `entity_id` `vacuum.mops` with the `entity_id` of your vacuum cleaner.  
- Click the **Run Action** button.

### 2. Home Assistant Xiaomi Miot Integration
- Install the integration [Xiaomi Miot Auto](https://github.com/al-one/hass-xiaomi-miot)

[![Add to HACS via My Home Assistant](https://my.home-assistant.io/badges/hacs_repository.svg)](https://my.home-assistant.io/redirect/hacs_repository/?owner=al-one&repository=hass-xiaomi-miot&category=integration)

In Home Assistant, go to **Developer Tools** → **Services** and switch to `YAML mode`.  
Paste the following code:

  ```yaml
  service: xiaomi_miot.set_miot_property
  data:
    entity_id: vacuum.dreame_p2041o_796c_robot_cleaner
    siid: 7 # siid for the audio service
    piid: 4 # piid for setting the voice pack
    value: '{"id":"UK","url":"https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz","md5":"3545e91c0626beccbd284469f6283a77","size":9620968}'
  
Replace the entity_id `vacuum.dreame_p2041o_796c_robot_cleaner` with the entity_id of your robot vacuum.

### 3. Python Miio (genericmiot)
Install [python-miio](https://github.com/rytilahti/python-miio) and run the following command:
```python
python -m miio.cli genericmiot --ip 192.168.50.157 --token 614a498f6c72506d6e3066764f73696a raw_command set_properties "[{'did': '8023334994', 'siid': 7, 'piid': 4, 'value' : '{\"id\":\"UK\",\"url\":\"https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz\",\"md5\":\"3545e91c0626beccbd284469f6283a77\",\"size\":9620968}'}]"
```

### 4. Python Miio (device)
```python
miiocli device --ip 192.168.50.157 --token 614a498f6c72506d6e3066764f73696a raw_command set_properties "[{'did': '8023334994', 'siid': 7, 'piid': 4, 'value' : '{\"id\":\"UK\",\"url\":\"https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz\",\"md5\":\"3545e91c0626beccbd284469f6283a77\",\"size\":9620968}'}]"
```

Replace the IP and token with your own.

### 5. Valetudo
```
- Open the Valetudo web interface by entering the IP address of your robot vacuum into your web browser.
- In Valetudo, go to "Robot Settings" -> "Misc Settings."
- Paste the following parameters into the "Voice packs" section:
    - URL: https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz
    - Language Code: UK
    - Hash: 3545e91c0626beccbd284469f6283a77
    - File size: 9620968
- Save and click "Set Voice Pack".
```
## 🎙️ How to create your own Dreame voice pack
- Prepare `.ogg` files, 16,000 Hz, Stereo/Mono according to the [phrase table](https://github.com/oleksandr-belei/dreame-vacuum-uk-voice-packs/blob/main/ua_voice_mapping.csv). You can create only 5-10 of the most popular phrases. Other phrases will be taken from the donor pack.

- Download any existing voice pack: [GLaDOS_ukr](https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/uk_glados_voice_pack.gz), [uk_female_pensive](https://github.com/oleksandr-belei/dreame-vacuum-uk-voice-packs/raw/refs/heads/main/voice_packs/uk_female_pensive), [dreame_female_uk](https://awsde0.fds.api.xiaomi.com/dreame-product/resources/59bcaf5201f15950c12917d0bb505321), [Les Poderevyansky](https://github.com/KonstantinDev7/Voice_Packs_for_Mi_Robot_S10_Plus/raw/refs/heads/main/Voice_Packs/LesV1ogg.tar.gz). A voice pack is a tar.gz archive. For example, the GLaDOS_ukr voice pack has a .gz extension. To open the archive, rename the extension from `.tar` to `tar.gz`. Similarly, you can add the extension to a pack that has no extension. Open the archive (on MacOS I used BetterZip) and replace the archive files with your own. Note: the archive must contain only files, not a folder with files.

- Upload the voice pack somewhere online to get a link to the file. For example, a public repository on GitHub, GitLab, FTP server, etc. Find out the file size in bytes and the md5 checksum of the file. If you don’t know how to do this, you can use online services.

## ⚙️ Installing the Roborock Voice Pack
[Demo video](https://www.youtube.com/shorts/RhcbOiGvVik?feature=share). This voice pack is intended to work on Roborock robot vacuums of the 1st and 2nd generation (v1, M1S, S4, S5, S5e, S6, S6_MaxV, S6_Pure, T6). I tested it on v1 (rockrobo.vacuum.v1, same as Gen 1 Xiaomi Mi SDJQRO2RR). Third-generation vacuums have voice packs signed with the Roborock certificate. Because of this, installing custom voice packs is not possible.

To install the voice pack:
1. Download [roborock_glados.pkg](https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/roborock_glados.pkg) to your computer;
2. Install [python-miio](https://github.com/rytilahti/python-miio);
3. In the command line, in the folder with roborock_glados.pkg, run the command
```python
mirobo --ip 192.168.0.124 --token 50597y49p1894f6d6e67477349747408 install-sound roborock_glados.pkg
```
where `192.168.0.124` should be replaced with the IP address of your robot vacuum, and `50597y49p1894f6d6e67477349747408` with your robot vacuum's token. You can find the token using the command `python -m miio.cli cloud list` (Windows), `miiocli cloud list` (Linux, MacOS), or any other convenient method like [this one](https://github.com/PiotrMachowski/Xiaomi-cloud-tokens-extractor).

## 🎙️ How to create your own Roborock voice pack
To create your own voice pack, you need to:
1. Create or download files in .wav format, bitrate 1411.2 KB/s, sample rate 44.1 or 16.0 kHz;
2. Download the encryption utility [ccrypt](https://ccrypt.sourceforge.net);
3. In the command line, in the folder with the files, run the command
```
tar zc *.wav | ccrypt -e -K "r0ckrobo#23456" > roborock_glados.pkg
```
where `roborock_glados` should be replaced with any name you want for your voice pack.
6. Done! You can upload the created .pkg file to your robot vacuum.

## ⚙️ Installing the Midea M7 Pro Voice Pack
* Download [SDK Platform Tools](https://developer.android.com/tools/releases/platform-tools) to your PC and extract them to any convenient folder.
* Connect the robot to your PC. The USB port is located under the top cover beneath the Reset button, hidden behind a plug.
* Open the command line in the extracted Platform Tools folder (right-click -> Open in Terminal) and run the command ```adb devices``` to make sure your device is recognized. If you see your device ID, everything is fine; if not, your cable may not support data transfer (I tried several cables I had and only one worked).
* Then download the [voice pack](https://github.com/sverdlyuk/glados_ukr/raw/refs/heads/main/GLaDOS%20Midea.zip) and extract it to any folder convenient for you.
* Create a text file in the Platform Tools folder with the following code:
```
@echo off
set SOURCE_FOLDER=full path to the folder with sounds
for /r “%SOURCE_FOLDER%” %%x in (*) do (
set “file=%%x”
setlocal enabledelayedexpansion
set “path=!file:%SOURCE_FOLDER%=!”
adb push “%%x” “/oem/sound/!path!”
endlocal
)
```
* Change the file extension from .txt to .bat, then run it.
* Done!

## 🎙️ How to create your own Midea M7 Pro voice pack
To create your own voice pack for Midea, simply prepare a folder with audio files in .mp3 format. Each file must meet the following specifications:
* Bitrate: 64 kbps (audio compression quality)
* Channels: mono (single-channel audio)
* Sample rate: 48000 Hz (number of audio samples per second)
File names must correspond to the numbers they represent. More details are in the [Midea command mapping file](https://github.com/sverdlyuk/glados_ukr/blob/main/midea_glados_uk_mapping.csv).
For convenience, here are the [original Midea M7 Pro sound files](https://github.com/sverdlyuk/glados_ukr/tree/main/Other%20files/original).

## 🎙️ How to create your own Xiaomi voice pack
A Xiaomi voice pack is a `tar.gz` archive containing `.mp3` files without folders (all files are placed directly in the root of the archive). All files are named with numbers. Each number corresponds to a specific phrase. See more details in the [Xiaomi command mapping](https://github.com/sverdlyuk/glados_ukr/blob/main/xiaomi_glados_uk_mapping.csv). The file bitrate is 96 kbps. The sample rate is 44.1 kHz or 16.0 kHz.

There is a difference in quality between low bitrate (e.g., 32 kbps) and higher bitrate (e.g., 96 or 120 kbps), but for short voice phrases it is almost unnoticeable. Therefore, it is recommended to use a bitrate in the range of 100–120 kbps for an optimal balance between quality and file size.

## 👏 Acknowledgements
Special thanks for the truly monumental work in creating this voice pack to [Lost Human](https://www.youtube.com/channel/UCZuVCATSHsgvBZMH-k3Gjcg).  
Thanks to everyone who financially supported this project. Without your donations, it would have been impossible. Thanks to [Oleksandr Belei](https://github.com/oleksandr-belei/dreame-vacuum-uk-voice-packs) for the Dreame phrase file used in this project.

## 💬 Support
If something remains unclear or you have difficulties with setup — feel free to ask for help. You can create a topic in the [Discussions tab](https://github.com/sverdlyuk/glados_ukr/discussions), write in the [Smart Home | Matrix chat](https://app.element.io/#/room/#selfhostedua:matrix.org), or leave a comment in the relevant [DOU topic](https://dou.ua/forums/topic/49563/).

🔧 If you notice inaccuracies or have ideas for improvement — I would sincerely appreciate your pull request or feedback.

## 📜 License
This project is open and available under the MIT license. You are free to use and modify it according to the license terms.
