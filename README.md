# Semesterarbeit_TipToi
Szenario:

Wir möchten ein Produkt herstellen mit dem Namen Tiptoi. "Tiptoi ist ein interaktives Lernspiel bestehend aus einem Digitalstift und einem Spielbrett, Buch oder Puzzle mit digitalem Papier."

Scope:

- Alle Anwendungen im "Ökosystem" TipToi des Herstellers
- Zwei Anwendungen (falls es Mehrere hat) mittels Use-Case-Diagramm beschreiben. Optional: Weitere Anwendungen.

Optional: Haben Sie in Ihrem Umfeld ein TipToi? Dann probieren sie das Produkt aus.

## Verteilungsdiagramm

Das Verteilungsdiagramm zeigt die physische Architektur des TipToi-Systems und die Kommunikation zwischen den beteiligten Geräten. Der PC bzw. Laptop dient als Client-Gerät, auf dem der TipToi Manager installiert ist. Über diesen werden Audiodateien, Produktaktivierungen und Firmware-Updates verwaltet. Der TipToi-Stift ist das zentrale Hardware-Gerät mit optischem Sensor (OID-Technologie), Lautsprecher, internem Speicher und USB-Schnittstelle.

Die Verbindung zwischen PC und Stift erfolgt hauptsächlich über USB zur Datenübertragung, optional auch über WLAN. Über den WLAN-Router besteht eine Netzwerkverbindung zum Ravensburger Server, der über einen TipToi-Webservice Audiodateien, Firmware-Updates und Produktinformationen bereitstellt. Die Kommunikation zwischen Stift bzw. PC und dem Server erfolgt über das HTTPS-Protokoll.

Das digitale Papier (OID) wie z. B. Bücher, Spielbretter oder Puzzles enthält unsichtbare Codes, die der Stift optisch erkennt, um die passenden Audioinhalte abzuspielen. Kabelgebundene Verbindungen (USB) sind durch durchgezogene Linien dargestellt, drahtlose Verbindungen (WLAN, OID) durch gestrichelte Linien.

## Glossar

| Begriff | Erklärung |
|----------|------------|
| **TipToi** | Interaktives Lernsystem von Ravensburger, bestehend aus einem digitalen Stift und Lernmaterialien mit unsichtbaren Codes (OID). |
| **TipToi Manager** | Desktop-Anwendung zur Verwaltung von Audiodateien, Firmware-Updates und Produktaktivierungen für den TipToi-Stift. |
| **OID (Optical Identification)** | Unsichtbare Punktmuster auf Büchern, Spielbrettern oder Puzzles, die vom Stift optisch erkannt werden. |
| **Firmware** | Interne Software des TipToi-Stifts, die grundlegende Funktionen und Audioausgabe steuert. |
| **Ravensburger Server** | Online-Dienst, der Audiodateien, Produktinformationen und Firmware-Updates für TipToi bereitstellt. |
| **HTTPS** | Verschlüsseltes Kommunikationsprotokoll für den sicheren Datenaustausch zwischen Geräten und Server. |
| **USB** | Physische Schnittstelle zur Verbindung und Datenübertragung zwischen PC und TipToi-Stift. |
| **WLAN** | Drahtloses Netzwerk, das optionale Kommunikation zwischen TipToi-Stift, PC und Server ermöglicht. |
| **Digitales Papier** | Gedrucktes Lernmaterial (z. B. Buch, Puzzle), das mithilfe von OID-Codes mit dem TipToi-Stift interagiert. |
| **Komponente** | Ein logisches Software-Modul (z. B. TipToi Manager oder Web-Service) innerhalb der Systemarchitektur. |
| **Device (Gerät)** | Physische Einheit im System, auf der Software-Komponenten oder Ausführungsumgebungen laufen (z. B. PC, Stift, Server). |


Quellen zu TipToi
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- Wikipedia: https://de.wikipedia.org/wiki/Tiptoi
- Offizielle Seite von Ravensburger: https://www.ravensburger.de/entdecken/ravensburger-marken/tiptoi/index.html
  - Serivce TipToi: https://service.ravensburger.de/tiptoi%C2%AE
- Spieleanleitungen: https://www.ravensburger.de/de-CH/service/spielanleitungen mit der Suche "TipToi", insbesondere:
  - tiptoi® Stift (00500) oder
  - tiptoi® Der Stift - WLAN-Edition, DLC_S6_Window_Clng_A3 (00036)
  - sowie eines der Bücher.
- Präsentation von Joachim Breitner "Der Tiptoi-Stift": https://youtu.be/GzXtgR73icg. Interessante Stellen: 04:00, 08:14, 11:04, 14:32, (15:42) zu 20:07, 51:21, 53:55.
- TipToi-Tool und ReverseEngineering: https://github.com/entropia/tip-toi-reveng mit wiki: https://github.com/entropia/tip-toi-reveng/wiki
- Interview ♦ Marco Teubner über Spiele für den Tiptoi
- (weniger relevant) Beitrag von srf zu Spieleentwicklung: https://www.srf.ch/radio-srf-3/digital/specials/computer-im-beruf/ulrich-blum-spieleautor-spiele-sind-anspruchsvoller-geworden
