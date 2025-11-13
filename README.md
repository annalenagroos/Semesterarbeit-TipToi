# TipToi

TipToi ist ein interaktives Lernsystem, welches Wissen auf spielerische und lebendige Weise vermittelt. Mit dem TipToi-Stift können Kinder Bücher, Spiele oder Puzzles entdecken, indem sie einfach auf Bilder oder Symbole tippen. Sofort ertönen passende Geräusche, Stimmen oder Erklärungen – so wird Lernen zu einem spannenden Erlebnis. Die TipToi-Anwendung auf dem Computer oder Tablet dient dazu, neue Inhalte auf den Stift zu laden und ihn mit verschiedenen Themenwelten zu erweitern. So können Kinder immer wieder Neues entdecken, selbstständig lernen und dabei jede Menge Spass haben.

# Architekturdokumentation der Software TipToi

Die Architekturdokumentation basiert auf dem Template von arc42[^1].

# Einführung und Ziele

*Kurze Beschreibung der Anwendung und Ziele des Business* 

## Funktionale Anforderungen

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


# Kontext & Abgrenzung

*Kontextdiagramm und Kurzbeschreibung.*

# Verteilungssicht

*Verteilungsdiagramm + Beschreibung*

Das Verteilungsdiagramm zeigt die physische Architektur des TipToi-Systems und die Kommunikation zwischen den beteiligten Geräten. Der PC bzw. Laptop dient als Client-Gerät, auf dem der TipToi Manager installiert ist. Über diesen werden Audiodateien, Produktaktivierungen und Firmware-Updates verwaltet. Der TipToi-Stift ist das zentrale Hardware-Gerät mit optischem Sensor (OID-Technologie), Lautsprecher, internem Speicher und USB-Schnittstelle.

Die Verbindung zwischen PC und Stift erfolgt hauptsächlich über USB zur Datenübertragung, optional auch über WLAN. Über den WLAN-Router besteht eine Netzwerkverbindung zum Ravensburger Server, der über einen TipToi-Webservice Audiodateien, Firmware-Updates und Produktinformationen bereitstellt. Die Kommunikation zwischen Stift bzw. PC und dem Server erfolgt über das HTTPS-Protokoll.

Das digitale Papier (OID) wie z. B. Bücher, Spielbretter oder Puzzles enthält unsichtbare Codes, die der Stift optisch erkennt, um die passenden Audioinhalte abzuspielen. Kabelgebundene Verbindungen (USB) sind durch durchgezogene Linien dargestellt, drahtlose Verbindungen (WLAN, OID) durch gestrichelte Linien.

# Qualitätsanforderungen

## QualitätsAnforderung-01 [QA-01]: Leistungseffizienz - Zeitverhalten

**Use Case:** UC-01 (Produkt aktivieren und spielen)  
**Kategorie:** Leistungseffizienz (Zeitverhalten)  
**Priorität:** Hoch

### Beschreibung
Ein Kind tippt mit dem tiptoi-Stift auf das Anmeldezeichen (grünes Power-Button-Symbol) eines neuen tiptoi-Buchs. Der Stift muss den OID-Code auslesen, die zugehörige Audiodatei (ca. 50 MB) im internen Speicher lokalisieren und die Wiedergabe starten. Das Kind erwartet eine sofortige Reaktion, um die Motivation zum Spielen aufrechtzuerhalten.

### Metrik
- **Maximale Reaktionszeit** vom Antippen bis zum Start der Audiowiedergabe: **< 1,5 Sekunden**
- **Erfolgsquote** bei korrekter Erkennung des OID-Codes beim ersten Versuch: **> 95%**
- **Maximale Suchzeit** im Dateisystem bei 50 installierten Produkten: **< 0,8 Sekunden**
- **CPU-Auslastung** während des Ladevorgangs: **< 60%** (um Akkuleistung zu schonen)

### Begründung
Die kurze Reaktionszeit ist entscheidend für die Kinderfreundlichkeit des Systems. Kinder haben eine kurze Aufmerksamkeitsspanne – Verzögerungen über 2 Sekunden führen zu Frustration und mehrfachem Antippen, was die Benutzererfahrung erheblich verschlechtert. Die Leistungseffizienz beeinflusst direkt die Akzeptanz des Produkts bei der Zielgruppe (Kinder 3-10 Jahre). Eine niedrige CPU-Auslastung verlängert zudem die Akkulaufzeit, was die Benutzbarkeit im Alltag verbessert.

---

## QA-02: Wartbarkeit - Modifizierbarkeit

**Use Case:** UC-06 (Stift-Inhalte verwalten)  
**Kategorie:** Wartbarkeit (Modifizierbarkeit)  
**Priorität:** Mittel

### Beschreibung
Ravensburger führt eine neue Produktkategorie "tiptoi Hörbücher" ein, die in der Verwaltungsansicht des tiptoi Managers separat angezeigt werden soll. Ein Entwickler muss die Funktion "Stift-Inhalte verwalten" erweitern, um die neue Kategorie mit eigenem Icon, Filterfunktion und Speicherplatz-Anzeige zu unterstützen. Die Änderung darf bestehende Funktionen (Anzeige von Büchern, Spielen, Stiften) nicht beeinträchtigen.

### Metrik
- **Implementierungszeit:** **< 8 Stunden** (1 Arbeitstag) für einen erfahrenen Entwickler
- **Anzahl betroffener Module:** Maximal **3 Module** (UI-Komponente, Datenmodell, Filter-Logik)
- **Regressionstests:** Bestehende Funktionen bleiben zu **100% funktionsfähig** (automatisierte Tests)
- **Code-Änderungen:** **< 200 Zeilen** neuer/geänderter Code
- **Deployment:** Keine Änderung der Datenbankstruktur oder Migration erforderlich

### Begründung
Die Modifizierbarkeit ist entscheidend für die Zukunftsfähigkeit des Systems. Ravensburger erweitert sein Produktportfolio kontinuierlich (ca. 3-5 neue Produktkategorien pro Jahr). Eine modulare Architektur mit klaren Schnittstellen ermöglicht schnelle Anpassungen ohne Risiko von Regressionsfehlern. Die geringe Anzahl betroffener Module zeigt eine gute Kapselung und reduziert Wartungskosten erheblich. Time-to-Market für neue Features wird durch hohe Wartbarkeit signifikant verkürzt.

---

## QA-03: Benutzbarkeit - Erlernbarkeit

**Use Case:** UC-03 (WLAN am Stift konfigurieren)  
**Kategorie:** Benutzbarkeit (Erlernbarkeit)  
**Priorität:** Hoch

### Beschreibung
Ein technisch unerfahrener Elternteil richtet erstmals die WLAN-Funktion des tiptoi-Stifts ein. Die Person schafft es, ohne Handbuch oder externe Hilfe innerhalb von 5 Minuten die WLAN-Verbindung erfolgreich zu konfigurieren und eine erste Audiodatei herunterzuladen.

### Metrik
- **Erfolgsquote:** **80% der Test-Nutzer** (ohne technische Vorkenntnisse) schaffen die Einrichtung in **< 5 Minuten**
- **Maximale Anzahl Fehler** während der Einrichtung: **2**
- **Erfolgsquote beim ersten Versuch:** **> 70%**

### Begründung
Die Erlernbarkeit ist kritisch für die Marktakzeptanz der WLAN-Edition. Die Hauptzielgruppe (Eltern mit Kindern 3-10 Jahre) hat sehr heterogene technische Vorkenntnisse. Eine intuitive Benutzerführung ohne Handbuchlektüre reduziert Support-Anfragen drastisch (geschätzt -40% Kosten) und verhindert negative Bewertungen aufgrund von Einrichtungsproblemen. Die 5-Minuten-Grenze orientiert sich an Usability-Standards für Consumer-Electronics (Nielsen Norman Group) und der durchschnittlichen Geduld von Eltern in Alltagssituationen.

# Glossar

| Begriff | Erklärung |
|----------|------------|
| **TipToi** | Interaktives Lernsystem von Ravensburger, bestehend aus einem digitalen Stift und Lernmaterialien mit unsichtbaren Codes (OID). |
| **TipToi Manager** | Desktop-Anwendung zur Verwaltung von Audiodateien, Firmware-Updates und Produktaktivierungen für den TipToi-Stift. |
| **OID (Optical Identification)** | Unsichtbare Punktmuster auf Büchern, Spielbrettern oder Puzzles, die vom Stift optisch erkannt werden. |
| **Firmware** | Interne Software des TipToi-Stifts, die grundlegende Funktionen und Audioausgabe steuert. |
| **Ravensburger Server** | Online-Dienst, der Audiodateien, Produktinformationen und Firmware-Updates für TipToi bereitstellt. |
| **HTTPS** | Verschlüsseltes Kommunikationsprotokoll für den sicheren Datenaustausch zwischen Geräten und Server. |
| **USB-Massenspeicher** | Der Stift wird am PC als externer Speicher erkannt |
| **WLAN-Edition** | Spezialausgabe des tiptoi-Stifts der 3. Generation mit integriertem WLAN-Modul |
| **Digitales Papier** | Gedrucktes Lernmaterial (z. B. Buch, Puzzle), das mithilfe von OID-Codes mit dem TipToi-Stift interagiert. |
| **Komponente** | Ein logisches Software-Modul (z. B. TipToi Manager oder Web-Service) innerhalb der Systemarchitektur. |
| **Device (Gerät)** | Physische Einheit im System, auf der Software-Komponenten oder Ausführungsumgebungen laufen (z. B. PC, Stift, Server). |
| **System-Grenze** | Grenze zwischen dem tiptoi Manager System und externen Akteuren/Systemen |
| **Anmeldezeichen** | Grünes Power-Button-Symbol auf der ersten Seite von tiptoi-Produkten zur Aktivierung |

---

## Quellen

- Ravensburger tiptoi Handbuch (Stift 3. Generation mit Aufnahmefunktion und WLAN)
- Ravensburger Serviceportal: service.ravensburger.de/tiptoi
- tiptoi Manager Download-Seite: ravensburger.de/tiptoi-manager
- Wikipedia: de.wikipedia.org/wiki/Tiptoi

---

[^1]: [arc42-Template](https://www.arc42.de/overview/)# Semesterarbeit_TipToi
