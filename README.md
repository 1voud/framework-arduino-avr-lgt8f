# framework-arduino-avr-lgt8f
framework-arduino-avr-lgt8f for LGT8F development in PlatformIO

Board package is taken from https://github.com/dbuezas/lgt8fx (current version > lgt8f-1.0.6 master 25-10-2020)

# How to use

## Prepare `328P-SSOP20.json`
Create `328P-SSOP20.json``.
```
{
    "build": {
      "core": "lgt8f",
      "extra_flags": "-DARDUINO_ARCH_AVR -DARDUINO_AVR_LARDU_328P -DAVR_LARDU_328E -DCLOCK_SOURCE=1,
      "f_cpu": "32000000L",
      "mcu": "atmega328p",
      "variant": "lgt8fx8ps20"
    },
    "bootloader": {
      "efuse": "0x07",
      "file": "lgt8fx8p/optiboot_lgt8f328p.hex",
      "hfuse": "0xFF",
      "lock_bits": "0x3F",
      "lfuse": "0xFF",
      "unlock_bits": "0x3F"
    },
    "frameworks": [
      "arduino"
    ],
    "name": "328P-SSOP20",
    "upload": {
      "maximum_ram_size": 2048,
      "maximum_size": 29696,
      "protocol": "arduino",
      "require_upload_port": true,
      "speed": 57600
    },
    "url": "https://www.arduino.cc/en/Main/ArduinoBoardNano",
    "vendor": "Arduino"
  }

```
Put this `json` file in PlatformIO project dir in the folder boards, such that you have the following structure:
```
rootproject\
    .pio\
    .vscode\
    boards\
        328P-SSOP20.json
    include\
    lib\
    src\
    test\
    platformio.ini
```

## Prepare `platformio.ini`
Create a `platformio.ini` with the following contents:
```
[env:328P-SSOP20]
platform = https://github.com/1voud/platform-atmelavr.git
framework = arduino
board = 328P-SSOP20
board_build.f_cpu=32000000L
board_build.clock_source=1
platform_packages = framework-arduino-avr-lgt8f@https://github.com/1voud/framework-arduino-avr-lgt8f.git

```
and build your project.
