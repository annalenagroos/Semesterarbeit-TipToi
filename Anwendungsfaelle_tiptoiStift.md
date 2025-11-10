# Use Case Spezifikation: tiptoi Manager WLAN Edition

**Projekt:** tiptoi Manager Anwendungsfallanalyse  
**Datum:** November 2025  
**Version:** 1.0

---

## UC-01: Produkt aktivieren und spielen

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-01 |
| **Name** | Produkt aktivieren und spielen |
| **Primärer Akteur** | Kind |
| **Sekundäre Akteure** | tiptoi-Stift, tiptoi-Produkt (Buch/Spiel) |
| **Vorbedingung** | - Audiodatei ist auf Stift geladen<br>- Stift ist eingeschaltet |
| **Beschreibung** | Das Kind tippt mit dem tiptoi-Stift auf das Anmeldezeichen (grünes Power-Button-Symbol) auf der ersten Doppelseite des tiptoi-Produkts. Der Stift liest den OID-Code aus dem Produkt und spielt die entsprechende Audiodatei ab. |
| **Nachbedingung** | Audiodatei wird abgespielt |
| **Quelle** | tiptoi Handbuch, Ravensburger Serviceportal |

---

## UC-02: Stift mit PC verbinden und erkennen (via USB)

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-02 |
| **Name** | Stift mit PC verbinden und erkennen (via USB) |
| **Primärer Akteur** | Eltern |
| **Sekundäre Akteure** | tiptoi-Stift |
| **Vorbedingung** | - tiptoi Manager ist installiert<br>- Stift ist eingeschaltet |
| **Beschreibung** | Verbinden Sie den eingeschalteten tiptoi-Stift mit Ihrem Rechner. Der tiptoi-Stift wird von der Software automatisch erkannt und als USB-Massenspeicher angezeigt. |
| **Nachbedingung** | Stift ist im Manager sichtbar und bereit für Dateiübertragung |
| **Quelle** | tiptoi Manager Anleitung |

---

## UC-03: WLAN am Stift konfigurieren

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-03 |
| **Name** | WLAN am Stift konfigurieren |
| **Primärer Akteur** | Eltern |
| **Sekundäre Akteure** | tiptoi-Stift, WLAN-Router |
| **Vorbedingung** | - Stift ist eingeschaltet<br>- WLAN-Zugangsdaten (SSID und Passwort) sind bekannt<br>- Ein WLAN-fähiges Hilfsgerät (Smartphone/Tablet/Laptop) ist verfügbar |
| **Beschreibung** | Zur Einrichtung der WLAN-Verbindung stellt der Stift kurzzeitig ein unverschlüsseltes WLAN-Netz bereit (tiptoi_TW...), mit dem sich ein Hilfsgerät verbinden kann. Über die IP-Adresse 192.168.1.1 im Browser werden dem Stift die WLAN-Zugangsdaten übergeben. Der Stift bestätigt die erfolgreiche Verbindung. |
| **Nachbedingung** | Stift ist mit dem WLAN-Netzwerk verbunden und kann Audiodateien drahtlos herunterladen |
| **Alternativer Ablauf** | Falls Verbindung fehlschlägt, Vorgang wiederholen oder Router-Einstellungen prüfen (MAC-Filter, Firewall) |
| **Quelle** | Ravensburger Serviceportal - WLAN einrichten |

---

## UC-04: Audiodatei suchen und herunterladen

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-04 |
| **Name** | Audiodatei suchen und herunterladen |
| **Primärer Akteur** | Eltern |
| **Sekundäre Akteure** | Ravensburger Server |
| **Vorbedingung** | - tiptoi Manager ist geöffnet<br>- Internetverbindung besteht |
| **Beschreibung** | Geben Sie in die Suchleiste den Titel Ihres tiptoi-Produkts ein und bestätigen Sie die Suche. Klicken Sie auf das Download-Icon an Ihrem tiptoi-Produkt. Der Download startet automatisch vom Ravensburger Server. |
| **Nachbedingung** | Audiodatei ist auf dem PC heruntergeladen und bereit zur Übertragung |
| **Quelle** | ravensburger.de/tiptoi-manager |

---

## UC-05: Audiodatei auf Stift übertragen

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-05 |
| **Name** | Audiodatei auf Stift übertragen |
| **Primärer Akteur** | Eltern |
| **Sekundäre Akteure** | tiptoi-Stift |
| **Vorbedingung** | - Stift ist per USB verbunden<br>- Audiodatei ist heruntergeladen |
| **Beschreibung** | Die Audiodatei wird automatisch auf den angeschlossenen tiptoi-Stift installiert. Der tiptoi Manager zeigt den Fortschritt an. |
| **Nachbedingung** | Audiodatei ist auf dem Stift verfügbar und kann vom Kind genutzt werden |
| **Alternativer Ablauf** | Bei WLAN-Edition: Audiodatei kann auch drahtlos per WLAN auf den Stift übertragen werden, wenn dieser mit dem Netzwerk verbunden ist |
| **Quelle** | tiptoi Manager Anleitung |

---

## UC-06: Stift-Inhalte verwalten

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-06 |
| **Name** | Stift-Inhalte verwalten |
| **Primärer Akteur** | Eltern |
| **Sekundäre Akteure** | tiptoi-Stift |
| **Vorbedingung** | - Stift ist mit PC verbunden<br>- tiptoi Manager ist geöffnet |
| **Beschreibung** | In der Navigation unter "Stift und Inhalte verwalten" finden Sie eine Liste Ihrer installierten Produkte. Nicht benötigte Audiodateien können gelöscht werden, um Speicherplatz freizugeben. Der Manager zeigt auch an, ob Aktualisierungen für installierte Produkte verfügbar sind. |
| **Nachbedingung** | Stift-Speicher ist optimiert und verwaltet |
| **Quelle** | tiptoi Manager Anleitung |

---

## UC-07: Firmware aktualisieren

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-07 |
| **Name** | Firmware aktualisieren |
| **Primärer Akteur** | Eltern |
| **Sekundäre Akteure** | tiptoi-Stift, Ravensburger Server |
| **Vorbedingung** | - Stift ist mit PC verbunden<br>- Neue Firmware-Version ist auf dem Server verfügbar<br>- Internetverbindung besteht |
| **Beschreibung** | Der tiptoi Manager informiert automatisch über verfügbare Firmware-Updates und hilft beim Aktualisieren des Betriebssystems des Stifts. Das Update wird heruntergeladen und auf den Stift übertragen. |
| **Nachbedingung** | Stift hat die aktuelle Firmware-Version installiert |
| **Hinweis** | Während des Updates darf der Stift nicht vom PC getrennt werden |
| **Quelle** | tiptoi Manager Anleitung |

---

## UC-08: Stift mit Energie versorgen / aufladen

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-08 |
| **Name** | Stift mit Energie versorgen / aufladen |
| **Primärer Akteur** | Eltern |
| **Sekundärer Akteur** | tiptoi-Stift |
| **Vorbedingung** | - Micro-USB-Kabel ist vorhanden<br>- USB-Netzteil (500mA-1A, 5V) oder PC mit USB-Anschluss ist verfügbar |
| **Beschreibung** | Der integrierte Akku des Stiftes (WLAN Edition) kann mit dem mitgelieferten Micro-USB-Kabel an einem Computer oder einem USB-Netzteil aufgeladen werden. Der Ladevorgang erfolgt bei Raumtemperatur. |
| **Nachbedingung** | Stift ist vollständig aufgeladen und einsatzbereit |
| **Hinweis** | Dieser Vorgang benötigt die tiptoi Manager Software nicht und ist daher außerhalb der System-Grenze. Der Stift darf nicht in direkter Sonne oder auf einem Heizkörper geladen werden. |
| **Quelle** | tiptoi Handbuch |

---

## UC-09: tiptoi Manager installieren

| Attribut | Beschreibung |
|----------|--------------|
| **Use Case ID** | UC-09 |
| **Name** | tiptoi Manager installieren |
| **Primärer Akteur** | Eltern |
| **System** | Betriebssystem (PC/Mac) |
| **Vorbedingung** | - Installationsdatei ist heruntergeladen<br>- PC/Mac erfüllt Systemanforderungen (Windows XP/Vista/7 oder neuer, Mac OS X ab 10.12) |
| **Beschreibung** | Die Installationsdatei für den tiptoi Manager wird auf dem PC oder Mac ausgeführt. Die Software führt durch den Installationsprozess. Nach der Installation kann der Manager gestartet und optional ein Benutzerkonto erstellt werden. |
| **Nachbedingung** | tiptoi Manager ist einsatzbereit und kann Stifte erkennen |
| **Hinweis** | Dies ist ein Vorbereitungsschritt und kein Use Case der tiptoi Manager Software selbst, daher außerhalb der System-Grenze. |
| **Quelle** | ravensburger.de/tiptoi-manager |

---

## Glossar

| Begriff | Beschreibung |
|---------|--------------|
| **OID-Code** | Optical Identification Code - versteckter Punkteraster-Code auf tiptoi-Produkten, der vom Stift gelesen wird |
| **Anmeldezeichen** | Grünes Power-Button-Symbol auf der ersten Seite von tiptoi-Produkten zur Aktivierung |
| **WLAN-Edition** | Spezialausgabe des tiptoi-Stifts der 3. Generation mit integriertem WLAN-Modul |
| **Audiodatei** | Digitale Sounddatei (.gme Format), die auf dem Stift gespeichert wird |
| **Firmware** | Betriebssystem des tiptoi-Stifts |
| **tiptoi Manager** | Desktop-Software (PC/Mac) zur Verwaltung von Audiodateien und Stift |
| **USB-Massenspeicher** | Der Stift wird am PC als externer Speicher erkannt |
| **Ravensburger Server** | Online-Server, von dem Audiodateien und Firmware-Updates heruntergeladen werden |
| **System-Grenze** | Grenze zwischen dem tiptoi Manager System und externen Akteuren/Systemen |

---

## Quellen

- Ravensburger tiptoi Handbuch (Stift 3. Generation mit Aufnahmefunktion und WLAN)
- Ravensburger Serviceportal: service.ravensburger.de/tiptoi
- tiptoi Manager Download-Seite: ravensburger.de/tiptoi-manager
- Wikipedia: de.wikipedia.org/wiki/Tiptoi

---

**Dokumentenende**