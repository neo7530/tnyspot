<img width="1509" height="804" alt="tnyspot" src="https://github.com/user-attachments/assets/dfb1d242-eeec-49b0-89c1-f2b90c6e56b8" />

# TNYSPOT – ESP32‑S3 DMR Hotspot

TNYSPOT ist ein kompakter, vollständig eigenständiger **DMR Simplex/Duplex Hotspot** auf Basis des  
**Waveshare ESP32‑S3 Zero**.  
Er bietet ein modernes Webinterface, Offline‑Talker‑Alias‑Erzeugung, programmierbare  
DMR‑ID‑ und Talkgruppen‑Downloads, einen integrierten POCSAG/DAPNET‑Sender sowie eine flexible  
Konfiguration direkt auf dem Gerät.

---

## 🚀 Features

### DMR
- **DMR Simplex & Duplex Hotspot** (MMDVM‑kompatibel)
- **Voice + Data, Group & Private**
- **Slot 1 & Slot 2** Unterstützung
- **JITTER‑Buffer** für stabilen Netzwerk‑Traffic
- **BER‑Messung** (Bit Error Rate) bei RF‑Empfang
- **Offline Talker‑Alias‑Erzeugung** direkt auf dem Gerät (generisch & Motorola‑kompatibel)
- **Verschlüsselungserkennung** — Encrypted Calls werden erkannt und angezeigt
- **SDS / Data‑Calls** — separates Log im Webinterface
- **Hangtime** konfigurierbar

### POCSAG / DAPNET
- **DAPNET‑TCP‑Client** (Port 43434) mit automatischer Wiederverbindung
- **POCSAG 1200 bps Sender** mit BCH(31,21)‑Fehlerkorrektur
- **Multi‑Batch‑Frames** — Nachrichten bis ~120 Zeichen (3 Batches)
- **Umlaut‑Transliteration** automatisch (ä→ae, ö→oe, ü→ue, ß→ss)
- **RIC‑Whitelist & Blacklist** mit Wildcard‑Unterstützung (`1234*`)
- **Wiederholungen** konfigurierbar (1–5×)
- **DMR hat immer Vorrang** — POCSAG wartet bis Modem nach Hangtime idle ist
- **Modemschutz** — DMR‑Netzwerkframes werden während POCSAG‑TX unterdrückt
- **DAPNET unabhängig** — Empfang und Logging auch bei deaktiviertem POCSAG‑Sender
- **Skyper‑Dekodierung** im Weblog automatisch (Erkennung + ASCII‑Shift‑Dekodierung, `[SKYPER]`‑Badge)

### OLED‑Display (128×64)
- **SSD1306** und **SH1106** unterstützt
- **Boot‑Logo** beim Start
- **Status‑Header** mit WiFi/AP/DMR‑Icons und Modus (IDLE / NET / RF / ENC)
- **Aktiver Call:** Rufzeichen groß (scrollend), Talkgroup darunter
- **Jitter‑Buffer‑Pegelanzeige** als Kastenbalken
- **POCSAG‑Modus:** RIC groß im Hauptfeld, Nachricht scrollend darunter
- **Uhranzeige** nach POCSAG‑Durchgang (HH:MM + DD.MM.YYYY)
- **Display‑Timeout** — automatisches Abschalten, bei Aktivität wieder ein

### Webinterface
- **Live‑Panels** für aktive Gespräche via WebSocket (NET / RF / ENC, animiert)
- **Tab: Gespräche** — Calllog mit Zeitstempel, Von/Zu, Dauer, Status
- **Tab: Data Log** — SDS/Data‑Calls separat
- **Tab: POCSAG Log** — letzte 10 Nachrichten (Zeitstempel, RIC, Text, Skyper‑Dekodierung)
- **POCSAG‑Lampe** im Header — leuchtet orange mit Glow‑Effekt während POCSAG sendet
- **Auto‑Refresh** mit Countdown‑Balken (pausierbar)
- **Konfigurationsseite** mit Tabs:

| Tab | Inhalt |
|---|---|
| Server | DMR‑Server, Port, DMR‑ID, Rufzeichen, Frequenzen, Farbcode, Leistung, UTC‑Offset, Passwörter |
| Modem | TX/RX‑Offset, Deviation, RF‑Leistung, Hangtime, Slots, Beacon |
| WiFi | Bis zu 5 WLAN‑Netzwerke (automatischer Fallback), AP‑Modus |
| Download | DMR‑ID‑Datenbank und Talkgroup‑Liste per URL laden |
| POCSAG | DAPNET‑Server/Callsign/Schlüssel, Frequenz, Wiederholungen, Whitelist/Blacklist |
| Lizenz | Lizenzkey‑Verwaltung |

### System & Konnektivität
- **Neopixel Status‑LED** mit Puls‑ und Farbmodi
- **Bis zu 5 WLAN‑Netzwerke** mit automatischem Fallback, AP‑Modus bei keinem bekannten Netz
- **FreeDMR / FDMR+ Optionszeile**
- **NTP‑Zeitsynchronisation** mit konfigurierbarem UTC‑Offset (−12 … +14 h)
- **OTA Firmware‑Update** direkt über das Webinterface
- **DMR‑ID‑Download** (TSV oder Semicolon‑getrennt, komprimierter Modus für >2 MB)
- **Talkgruppen‑Download** (CSV)
- **USB‑Passthrough‑Modus** für direkten Modemzugriff
- Alle Einstellungen im **NVS** (Non‑Volatile Storage) gespeichert
- HTML‑Seiten **GZIP‑komprimiert im Flash** (PROGMEM) — kein SPIFFS nötig

### Lizenzsystem
- Ohne Lizenz: **RX‑only**, kein Talker‑Alias, TX gesperrt
- Mit Lizenz: **TX + Talker‑Alias freigeschaltet**
- Lizenz ist an die **Chip‑ID** des ESP32‑S3 gebunden
- Prüfung offline, sicher signiert, keine Cloud‑Abhängigkeit

---

## 🔧 Hardware: Waveshare ESP32‑S3 Zero

Der TNYSPOT ist optimiert für den **Waveshare ESP32‑S3 Zero**.  
(Für weitere Hardware‑Unterstützung, Pinbelegungen etc. bitte per Mail Kontakt aufnehmen. **WICHTIG:** PSRAM wird dringend benötigt)

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

---

## 🛠️ Aufbauanleitung

### 1. Firmware flashen
ESP32‑S3 Zero per USB‑C anschließen und Firmware mit dem **flash_download_tool** von Espressif flashen.  
Gerät startet automatisch im Access‑Point‑Modus.

### 2. OLED anschließen (SSD1306 oder SH1106, 128×64)
- SDA → Pin 6  
- SCL → Pin 5  
- VCC → 3,3 V  
- GND → GND

### 3. MMDVM‑Modem anschließen
TX/RX kreuzen:
- Modem TX → ESP32 Pin 4  
- Modem RX → ESP32 Pin 3  
- Wakeup → Pin 7  
- BOOT0 → Pin 8  
- GND verbinden  
- 3,3 V oder 5 V je nach Modem

### 4. Webinterface öffnen
Nach dem Start erzeugt der Hotspot einen Access‑Point:
- **SSID:** `TNYSPOT_Config`
- **Passwort:** `TINYSPOT`

Webinterface: `http://192.168.4.1`  
Webinterface‑Passwort (Default): `TNYSPOT`

---

## 🌐 WLAN & Netzwerke

Der TNYSPOT speichert bis zu 5 WLAN‑Netzwerke. Falls kein bekanntes WLAN gefunden wird → AP‑Modus.

Unterstützte Netzwerke:
- FreeDMR
- FDMR+
- Private Master
- Custom Server (manuell konfigurierbar)

---

## 📥 DMR‑ID & Talkgruppen Download

**DMR‑ID‑Listen** — unterstützt:
- TSV
- Semicolon‑getrennte Dateien

> ⚠️ **Hinweis:** Bei Dateien größer als 2 MB bitte den Haken **„Komprimiere Download"** aktivieren.  
> Dann werden die Daten gestreamt, nicht vollständig in den PSRAM geladen.

**Talkgruppen** — CSV‑Format, automatische Zuordnung, Offline‑Speicherung.

---

## 🔐 Lizenzsystem

| | Ohne Lizenz | Mit Lizenz |
|---|---|---|
| RX (Gespräche hören) | ✅ | ✅ |
| Talker‑Alias | ❌ | ✅ |
| TX (Senden) | ❌ | ✅ |

---

## 🔒 Sicherheit

- Webinterface‑Passwort änderbar
- Hotspot‑AP‑Passwort änderbar
- Lizenzprüfung offline, sicher signiert
- Keine Cloud‑Abhängigkeit

---

## 📦 Geplante Features / Ideen

- Multi‑Mode (D‑STAR, YSF, GPS)
- Nextion Display
- Bluetooth‑Konfiguration
- Erweiterte UI‑Widgets
- Automatische Master‑Liste

---

## 📧 Kontakt

Fragen, Support oder Lizenzanfragen:

**E‑Mail:** tnyspot@dynbox.cloud

---

## 📄 Lizenz

Dieses Projekt ist proprietär.  
Die Nutzung der TX‑Funktion erfordert eine gültige Lizenz.

```
Ohne Lizenz: RX‑only
Mit Lizenz:  TX freigeschaltet
```

Viel Spaß mit dem TNYSPOT!
