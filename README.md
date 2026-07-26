# Brink Flair 400 ESPHome Modbus

ESPHome-Konfiguration zur lokalen Einbindung einer Brink Flair 400
Lüftungsanlage in Home Assistant über Modbus RTU.

## Zielhardware

- Brink Flair 400 Standard UWA2-B
- M5Stack AtomS3 Lite
- M5Stack Atomic RS485 Base
- Modbus RTU: Adresse 20, 19.200 Baud, gerade Parität, 1 Stopbit

Andere Flair-Modelle oder Hardwarevarianten können abweichende Register,
Adressen und GPIOs verwenden. Vor dem Flashen müssen diese Angaben mit der
eigenen Anlage abgeglichen werden.

## Funktionen

- Temperaturen, Feuchte, Luftmengen, Drücke und Ventilatordrehzahlen
- Bypass-, Frostschutz- und Filterstatus
- Wahl des Betriebsmodus und der Lüfterstufe
- Filter-Reset, Bypass-Boost und weitere Einstellwerte
- Rücklesekontrolle für Modbus-Schreibbefehle
- Home-Assistant-API, lokaler Webserver und OTA-Updates

Beim Start und beim Verbindungsaufbau werden keine Modbus-Schreibbefehle
ausgeführt. Schreibbefehle werden erst durch eine ausdrückliche Bedienaktion
ausgelöst.

## Installation

1. `brinkflair400.yaml` in das ESPHome-Verzeichnis kopieren.
2. `secrets.example.yaml` als `secrets.yaml` kopieren.
3. Alle Beispielwerte in `secrets.yaml` durch eigene Zugangsdaten und zufällige
   Schlüssel ersetzen.
4. Die GPIO-Belegung, Modbus-Adresse und Geräteeinstellungen prüfen.
5. Die Konfiguration in ESPHome validieren und anschließend auf den ESP32
   installieren.
6. Das automatisch erkannte ESPHome-Gerät in Home Assistant hinzufügen.

Beispiel für eine lokale Validierung:

```shell
esphome config brinkflair400.yaml
```

`secrets.yaml` ist durch `.gitignore` von Git ausgeschlossen.

## Sicherheit

Die Lüftungsanlage vor Arbeiten an Anschlussklemmen vollständig spannungsfrei
schalten. Modbus-Schreibbefehle können den Betriebszustand der Anlage verändern.
Register und Werte deshalb nur verwenden, wenn sie zur eigenen Geräte- und
Firmwareversion passen.

Die API, OTA-Schnittstelle, der Fallback-Hotspot und der Webserver verwenden
Werte aus `secrets.yaml`. Das ESPHome-Gerät und Home Assistant sollten nicht
ungeschützt aus dem Internet erreichbar sein.

## Herkunft und Lizenz

Die Standalone-Konfiguration wurde aus
[fonske/Brink-flair-modbus](https://github.com/fonske/Brink-flair-modbus)
abgeleitet und für Brink Flair 400, M5Stack AtomS3 Lite sowie explizit
ausgelöste und rückgelesene Steuerbefehle angepasst.

Dieses Projekt steht entsprechend dem Ursprungsprojekt unter der
GNU General Public License Version 3 oder später. Siehe `LICENSE`.

Brink ist eine Marke des jeweiligen Rechteinhabers. Dieses Community-Projekt
ist nicht mit dem Hersteller verbunden und wird nicht von ihm unterstützt.
