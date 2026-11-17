# Capricorn Firmware

<p>
  <a href="https://github.com/aule-org/capricorn-hw"><img src="https://img.shields.io/badge/Hardware-capricorn--hw-1f6feb.svg" alt="Capricorn hardware"></a>
  <a href="https://github.com/aule-org/capricorn-fw"><img src="https://img.shields.io/badge/Firmware-Capricorn-2da44e.svg" alt="Capricorn firmware"></a>
  <a href="https://github.com/aule-org/capricorn-sw"><img src="https://img.shields.io/badge/Server-capricorn--sw-d97706.svg" alt="Capricorn server"></a>
  <a href="https://github.com/aule-org/capricorn-app"><img src="https://img.shields.io/badge/App-capricorn--app-8250df.svg" alt="Capricorn app"></a>
  <a href="https://github.com/78/xiaozhi-esp32"><img src="https://img.shields.io/badge/Based%20on-xiaozhi--esp32-555.svg" alt="Based on xiaozhi-esp32"></a>
</p>

(English | [Español](README.es.md))

**Capricorn is the open-source AI tutor.** This repository is its firmware: the software that runs on the device, listens to the child, speaks back and draws the lesson on the e-ink page.

We did not start from zero, and we do not want to. Capricorn's firmware is a fork of [xiaozhi-esp32](https://github.com/78/xiaozhi-esp32), the most widely used open-source voice-AI firmware for ESP32. We add what a tutor for children needs on top of it, and we send everything generic back upstream.

## What we add

- **A LiveKit transport.** Voice over WebRTC with [LiveKit](https://github.com/livekit/client-sdk-esp32), next to xiaozhi's WebSocket and MQTT transports. It connects the device to any [LiveKit Agents](https://github.com/livekit/agents) tutor, such as our server, [capricorn-sw](https://github.com/aule-org/capricorn-sw), and lets a parent or a human tutor join the same session.
- **The Capricorn board.** Support for the [capricorn-hw](https://github.com/aule-org/capricorn-hw) device: 7.5" e-ink with touch, physical microphone mute, wake on motion.
- **A tutor interface for e-ink.** Exercises, hints and progress designed for a page, not a phone screen.
- **Lessons from the field.** Pieces from our earlier device, which families used at home: Bluetooth and browser Wi-Fi setup, per-device credentials and audio-dropout concealment tuned on real home networks.

## Branches

| Branch | Purpose |
|---|---|
| `capricorn` (default) | Our work. |
| `main` | Mirrors [78/xiaozhi-esp32](https://github.com/78/xiaozhi-esp32). Never edited by hand. |

Contributions meant for xiaozhi go to xiaozhi as pull requests from topic branches. We already contribute upstream on the LiveKit side: [livekit/client-sdk-esp32#74](https://github.com/livekit/client-sdk-esp32/pull/74).

## Status

Early. The LiveKit transport and the Capricorn board support are being written; there is nothing to flash yet. Until then, the code on `main` is plain xiaozhi and its own [documentation](https://github.com/78/xiaozhi-esp32#readme) applies.

## License

MIT, the same license as xiaozhi-esp32. See [LICENSE](../LICENSE). xiaozhi-esp32 is © Shenzhen Xinzhi Future Technology Co., Ltd.; Capricorn additions are © Aule.

---

Made in Lima, Peru by [Aule](https://meetaule.com) · admin@meetaule.com
