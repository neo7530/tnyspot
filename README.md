
<img width="1509" height="804" alt="tnyspot" src="https://github.com/user-attachments/assets/dfb1d242-eeec-49b0-89c1-f2b90c6e56b8" />
# TNYSPOT – ESP32‑S3 DMR Hotspot

TNYSPOT ist ein kompakter, vollständig eigenständiger **DMR Simplex Hotspot** auf Basis des  
**Waveshare ESP32‑S3 Zero**.  
Er bietet ein modernes Webinterface, Offline‑Talker‑Alias‑Erzeugung, programmierbare  
DMR‑ID‑ und Talkgruppen‑Downloads sowie eine flexible Konfiguration direkt auf dem Gerät.

---

## 🚀 Features

- **DMR Simplex Hotspot** (MMDVM‑kompatibel)
- **Neopixel Status-Anzeige**
- **Voice + Data, Group & private**
- **JITTER-Buffer für Netzwerk-Traffic**
- **Webinterface** zur Konfiguration (WLAN, Netzwerk, Optionen, Lizenz)
- **Offline Talker‑Alias‑Erzeugung** direkt auf dem Gerät (Motorola-kompatibel)
- **DMR‑ID‑Download** (TSV oder Semicolon‑getrennt)
- **Talkgruppen‑Download** (CSV)
- **Komprimierter Download** für große DMR‑ID‑Dateien (>2 MB)
- **Speicher für bis zu 5 WLAN‑Netzwerke**
- **FreeDMR / FDMR+ Optionszeile**
- **Passwortänderung für Hotspot‑AP und Webinterface**
- **OLED‑Display‑Unterstützung (SSD1306)**
- **Lizenzsystem** (RX‑only ohne Lizenz, TX‑Freischaltung mit gültiger Lizenz)

---

## 🔧 Hardware: Waveshare ESP32‑S3 Zero

Der TNYSPOT ist optimiert für den **Waveshare ESP32‑S3 Zero**.
(Für weitere Hardware-Unterstützung, Pinbelegungen etc. bitte per Mail Kontakt aufnehmen. **WICHTIG:** PSRAM wird dringend benötigt)

### 📌 Pinbelegung
<img width="1920" height="1082" alt="back" src="https://github.com/user-attachments/assets/5b261336-107b-41dd-94ac-fbb432844039" />

<img width="1920" height="1082" alt="vorderseite" src="https://github.com/user-attachments/assets/fcaec09a-577a-44bf-a7ce-122a05759341" />

| Funktion                 | ESP32‑S3 Pin |
|-------------------------|--------------|
| MMDVM RX (Modem → ESP)  | **4**        |
| MMDVM TX (ESP → Modem)  | **3**        |
| Modem Wakeup            | **7**        |
| Modem BOOT0             | **8**        |
| OLED SDA                | **6**        |
| OLED SCL                | **5**        |

🛠️ Aufbauanleitung
1. ESP32‑S3 Zero vorbereiten
ESP32‑S3 Zero per USB‑C anschließen

Firmware mit flash_download_tool von Espressif flashen

Gerät startet automatisch im Access‑Point‑Modus

2. OLED anschließen (SSD1306, 128x64)
SDA → Pin 6

SCL → Pin 5

VCC → 3.3V

GND → GND

3. MMDVM‑Modem anschließen
TX/RX kreuzen:

Modem TX → ESP32 Pin 4

Modem RX → ESP32 Pin 3

Wakeup → Pin 7

BOOT0 → Pin 8

GND verbinden

3.3V oder 5V je nach Modem

4. Webinterface öffnen
Nach dem Start erzeugt der Hotspot einen Access‑Point:

SSID: TNYSPOT_Config

Passwort: TINYSPOT

Webinterface öffnen unter:

Code
http://192.168.4.1
Webinterface‑Passwort (Default): TNYSPOT

🌐 WLAN & Netzwerke
Der TNYSPOT speichert bis zu 5 WLAN‑Netzwerke.
Falls kein bekanntes WLAN gefunden wird → AP‑Modus.

Unterstützte Netzwerke:

FreeDMR

FDMR+

Private Master

Custom Server (manuell konfigurierbar)

📥 DMR‑ID & Talkgruppen Download
DMR‑ID‑Listen
Unterstützt:

TSV

Semicolon‑getrennte Dateien

⚠️ WICHTIGER HINWEIS
Bei Dateien größer als 2 MB:

👉 Bitte den Haken „Komprimiere Download“ aktivieren.

Dann werden die Daten gestreamt, nicht vollständig in den PSRAM geladen.
So wird nur so viel gespeichert, wie der RAM zulässt.

Talkgruppen
CSV‑Format

Automatische Zuordnung

Offline‑Speicherung

🔐 Lizenzsystem
Ohne Lizenz:

RX‑only, kein Talker-Alias

Gespräche aus dem Netzwerk können gehört werden

TX ist gesperrt

Mit Lizenz:

TX und Talker-Alias wird freigeschaltet

Lizenz ist an die Chip‑ID des ESP32‑S3 gebunden


🔒 Sicherheit
Webinterface‑Passwort änderbar

Hotspot‑AP‑Passwort änderbar

Lizenzprüfung offline, sicher signiert

Keine Cloud‑Abhängigkeit

📦 Geplante Features / Ideen
Multi‑Mode (D‑STAR, YSF, POCSAG / DAPNET, GPS)

Nextion Display

DMR Duplex-Betrieb

Bluetooth‑Konfiguration

Erweiterte UI‑Widgets

Automatische Master‑Liste

📧 Kontakt
Fragen, Support oder Lizenzanfragen:

E‑Mail:  
tnyspot@von-ziemdorf.de

📄 Lizenz
Dieses Projekt ist proprietär.
Die Nutzung der TX‑Funktion erfordert eine gültige Lizenz.

Code
Ohne Lizenz: RX‑only
Mit Lizenz: TX freigeschaltet
Viel Spaß mit dem TNYSPOT!
