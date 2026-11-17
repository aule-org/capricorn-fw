# Capricorn Firmware

<p>
  <a href="https://github.com/aule-org/capricorn-hw"><img src="https://img.shields.io/badge/Hardware-capricorn--hw-1f6feb.svg" alt="Hardware de Capricorn"></a>
  <a href="https://github.com/aule-org/capricorn-fw"><img src="https://img.shields.io/badge/Firmware-Capricorn-2da44e.svg" alt="Firmware de Capricorn"></a>
  <a href="https://github.com/aule-org/capricorn-sw"><img src="https://img.shields.io/badge/Servidor-capricorn--sw-d97706.svg" alt="Servidor de Capricorn"></a>
  <a href="https://github.com/aule-org/capricorn-app"><img src="https://img.shields.io/badge/App-capricorn--app-8250df.svg" alt="App de Capricorn"></a>
  <a href="https://github.com/78/xiaozhi-esp32"><img src="https://img.shields.io/badge/Basado%20en-xiaozhi--esp32-555.svg" alt="Basado en xiaozhi-esp32"></a>
</p>

([English](README.md) | Español)

**Capricorn es el tutor de IA de código abierto.** Este repositorio es su firmware: el software que corre en el aparato, escucha al niño, le responde y dibuja la lección en la página de tinta electrónica.

No empezamos de cero, ni queremos hacerlo. El firmware de Capricorn es un fork de [xiaozhi-esp32](https://github.com/78/xiaozhi-esp32), el firmware abierto de voz con IA para ESP32 más usado. Encima le agregamos lo que necesita un tutor para niños, y todo lo que sirva en general lo devolvemos al proyecto original.

## Lo que agregamos

- **Un transporte LiveKit.** Voz por WebRTC con [LiveKit](https://github.com/livekit/client-sdk-esp32), junto a los transportes WebSocket y MQTT de xiaozhi. Conecta el aparato con cualquier tutor hecho en [LiveKit Agents](https://github.com/livekit/agents), como nuestro servidor, [capricorn-sw](https://github.com/aule-org/capricorn-sw), y permite que un padre o un tutor humano entre a la misma sesión.
- **La placa de Capricorn.** Soporte para el aparato de [capricorn-hw](https://github.com/aule-org/capricorn-hw): tinta electrónica de 7.5" con táctil, silencio físico del micrófono, despertar con movimiento.
- **Una interfaz de tutor para tinta electrónica.** Ejercicios, pistas y avance pensados para una página, no para la pantalla de un celular.
- **Lo aprendido en el campo.** Piezas de nuestro aparato anterior, que familias usaron en casa: configuración del Wi-Fi por Bluetooth y por navegador, credenciales por aparato y ocultamiento de cortes de audio afinado en redes domésticas reales.

## Ramas

`capricorn` es la única rama y la que se ve por defecto. xiaozhi no se copia en este repositorio: se sigue como remoto, y sus cambios entran con un pull request que fusiona su `main` en `capricorn`.

```bash
git remote add upstream https://github.com/78/xiaozhi-esp32.git
git fetch upstream
git switch -c sync/xiaozhi-$(date +%Y-%m-%d) origin/capricorn
git merge upstream/main          # luego abre un pull request a capricorn
```

Si una sincronización toca los formularios de issues de xiaozhi o `SUPPORT.md`, mantenlos borrados: este repositorio usa sus propios formularios en `.github/ISSUE_TEMPLATE/`.

Lo que sirva a xiaozhi se le envía como pull request desde ramas basadas en `upstream/main`. Los nombres de rama no deben empezar con `ci/`: el workflow de compilación de xiaozhi corre su matriz completa en esas ramas. Del lado de LiveKit ya contribuimos: [livekit/client-sdk-esp32#74](https://github.com/livekit/client-sdk-esp32/pull/74).

## Estado

Temprano. Cada push y pull request compila la placa de Capricorn y dos placas de referencia en GitHub Actions. El soporte de la placa cubre el audio, el botón para hablar y el LED de estado; siguen la pantalla de tinta electrónica, el táctil y el transporte LiveKit. Nada se ha ejecutado todavía en una placa de Capricorn.

## Licencia

MIT, la misma licencia de xiaozhi-esp32. Ver [LICENSE](../LICENSE). xiaozhi-esp32 es © Shenzhen Xinzhi Future Technology Co., Ltd.; lo que agrega Capricorn es © Aule.

---

Hecho en Lima, Perú, por [Aule](https://meetaule.com) · admin@meetaule.com
