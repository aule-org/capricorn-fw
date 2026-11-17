# Aule Capricorn v0.2

Board support for [Capricorn](https://github.com/aule-org/capricorn-hw), the open-source AI tutor: ESP32-S3-WROOM-1 (16 MB flash, 8 MB octal PSRAM), ES7210 + ES8311 audio with a speaker reference for echo cancellation, PAM8302A amplifier, 7.5" e-ink with GT911 touch, a talk button and a hardware microphone mute.

## Status

| Feature | State |
|---|---|
| Audio power switch (Q1), codecs, amplifier | Implemented, not yet tested on hardware |
| Talk button (SW1), status LED | Implemented, not yet tested on hardware |
| Hardware microphone mute (SW6) | Read at boot; the switch itself works without firmware |
| E-ink display (UC8179) and GT911 touch | Not yet: next step |
| Battery level, accelerometer wake | Not yet |

The microphone and reference gains in `config.h` are starting values from the board's level budget, not measurements.

## Notes

- The codecs and the audio I2C pull-ups are powered through Q1 (`AUDIO_POWER_EN_GPIO`, low = on), so audio is powered before the I2C bus is created.
- The touch controller has its own I2C bus, and its address is latched at reset from the INT pin, which has no resistor on the board. The driver must run the GT911 reset sequence described in `config.h`.
- Pin map source: [capricorn-hw/software](https://github.com/aule-org/capricorn-hw/tree/main/software).
