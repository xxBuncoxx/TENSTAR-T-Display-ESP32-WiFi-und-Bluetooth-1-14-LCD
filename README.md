Ein TTGO T-Display CGM-Projekt für Dexcom ist ein hervorragendes DIY-Vorhaben. Das kompakte LilyGO TTGO T-Display (basiert auf dem ESP32-Mikrocontroller mit integriertem WLAN und Bluetooth) eignet sich ideal als kleiner, energiesparender Desktop-Monitor oder als Nachtschrank-Uhr, um den aktuellen Blutzuckerwert und die Trendpfeile in Echtzeit anzuzeigen.
Wie funktioniert das Projekt?
Da der ESP32 über WLAN verfügt, verbindet sich das Board mit dem Internet und ruft die Daten typischerweise aus der folgenden Quelle ab:
Dexcom Share API: Das Board loggt sich mit Ihren offiziellen Dexcom-Zugangsdaten (denen der „Follower“-App) ein und holt die Werte alle 5 Minuten direkt von den Dexcom-Servern ab.

Was Sie für den Start benötigen
1.	Hardware: Ein LilyGO TTGO T-Display (entweder das klassische ESP32 V1.1 mit 1.14" Display oder das neuere T-Display-S3).
(https://short-url.cc/1Hvyj) oder (https://short-url.cc/1Hvyt)

3.	Entwicklungsumgebung: Die Arduino IDE oder VS Code mit PlatformIO.
4.	Wichtige Software-Bibliotheken (falls Sie selbst coden):
o	TFT_eSPI (für die Grafikausgabe auf dem ST7789 Display-Treiber).
o	WiFi.h und HTTPClient.h (für die Internetverbindung und HTTPS-Abfragen an Dexcom/Nightscout).
o	ArduinoJson (zum Verarbeiten der API-Antworten).

Für das klassische TTGO T-Display (ESP32 mit dem kleinen 1.14 Zoll Bildschirm und dem ST7789-Treiber) lässt sich ein CGM-Monitor fantastisch umsetzen. Dank der integrierten Tasten und des kompakten Formfaktors hast du im Handumdrehen eine unauffällige Blutzuckeruhr.

Hier die komplette Anleitung, wie du den Code über die Arduino IDE auf dein TENSTAR T-Display flashst:
1. Arduino IDE vorbereiten
Lade die neueste Arduino IDE herunter (Version 2.x empfohlen): https://www.arduino.cc/en/software
Öffne die Arduino IDE.

2. ESP32 Board-Support installieren
Gehe zu Datei → Voreinstellungen (Preferences)
Bei Zusätzliche Boardverwalter-URLs folgendes eintragen: https://espressif.github.io/arduino-esp32/package_esp32_index.json
Klicke auf OK
Gehe zu Werkzeuge → Board → Boards Manager
Suche nach esp32 und installiere esp32 by Espressif Systems (neueste Version)

3. Benötigte Bibliotheken installieren
Gehe zu Sketch → Bibliothek einbinden → Bibliotheken verwalten und installiere folgende Bibliotheken:

Adafruit ST7789
Adafruit GFX
ArduinoJson
WiFiManager (by tzapu)

4. Board einstellen
Unter Werkzeuge wählst du folgende Einstellungen:

Board	ESP32 Dev Module
Upload Speed	921600
CPU Frequency	240MHz
Flash Frequency	80MHz
Flash Mode	QIO
Flash Size	4MB (oder 16MB, je nach Board)
Partition Scheme	Default 4MB with spiffs
Port	Den COM-Port deines Boards

5. Code hochladen
Erstelle einen neuen Sketch (Strg + N)
Lösche den kompletten Inhalt
Füge den kompletten angepassten Code ein, den ich dir gegeben habe
Speichere den Sketch (z. B. als Dexcom_TDisplay)
Verbinde dein TENSTAR T-Display per USB-C
Wähle den richtigen COM-Port unter Werkzeuge → Port
Klicke auf den Upload-Button (Pfeil nach rechts)
________________________________________
Tipps bei Problemen
•	Upload schlägt fehl?
Halte den BOOT-Button (linker Button) gedrückt, während du auf Upload klickst, und lasse ihn erst los, wenn „Connecting…“ erscheint.
•	Falscher COM-Port?
Unter Windows: Geräte-Manager → Anschlüsse (COM & LPT)
Unter dem Board steht meist „USB-SERIAL CH9102“ oder „Silicon Labs“.
•	Display bleibt schwarz?
Prüfe, ob die Bibliothek Adafruit ST7735 and ST7789 richtig installiert ist.
