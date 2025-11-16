# tiptoi

TipToi ist ein interaktives Lernsystem, welches Wissen auf spielerische und lebendige Weise vermittelt. Mit dem tiptoi-Stift können Kinder Bücher, Spiele oder Puzzles entdecken, indem sie einfach auf Bilder oder Symbole tippen. Sofort ertönen passende Geräusche, Stimmen oder Erklärungen – so wird Lernen zu einem spannenden Erlebnis. Die tiptoi-Anwendung auf dem Computer oder Tablet dient dazu, neue Inhalte auf den Stift zu laden und ihn mit verschiedenen Themenwelten zu erweitern. So können Kinder immer wieder Neues entdecken, selbstständig lernen und dabei jede Menge Spass haben.

# Architekturdokumentation der Software tiptoi

Die Architekturdokumentation basiert auf dem Template von arc42[^1].

# Einführung und Ziele

Diese Architekturdokumentation beschreibt Aufbau, Struktur und technische Zusammenhänge des tiptoi-Systems bestehend aus tiptoi-Stift, tiptoi Manager und der Content-Plattform von Ravensburger. Ziel ist es, die relevanten Komponenten, Datenflüsse und Schnittstellen so darzustellen, dass Wartung, Weiterentwicklung und Analyse des Systems nachvollziehbar möglich sind.
Die Dokumentation richtet sich an Entwickler, Architekten und Studierende, die ein einheitliches Verständnis über die Systemarchitektur benötigen. Der Schwerpunkt liegt auf der Modellierung der Kernfunktionen wie Produktaktivierung, Inhaltsverwaltung, Firmware-Updates und der Kommunikation zwischen Stift, Manager und Backend.
Darüber hinaus definiert dieses Kapitel die fachlichen und technischen Ziele des Systems: zuverlässige Bereitstellung digitaler Inhalte, sichere Datenübertragung, offline-fähige Nutzung sowie eine benutzerfreundliche Verwaltung durch Eltern. Die beschriebenen Modelle dienen als Grundlage für die folgenden architektonischen Sichten und Qualitätsanforderungen. 

## Funktionale Anforderungen

### Anwendungsfall tiptoi-Manager

![Anwendungsfalldiagramm tiptoi-Manager](/Anwendungsfalldiagramm_TipToi.png)

#### UC-01: Produkt aktivieren und spielen
Das Kind tippt mit dem tiptoi-Stift auf das Anmeldezeichen (grünes Power-Button-Symbol) auf der ersten Doppelseite des tiptoi-Produkts. Der Stift liest den OID-Code aus dem Produkt und spielt die entsprechende Audiodatei ab.

#### UC-02: Stift mit PC verbinden und erkennen (via USB)
Verbindet den eingeschalteten tiptoi-Stift mit dem Rechner des Benutzers. Der tiptoi-Stift wird von der Software automatisch erkannt und als USB-Massenspeicher angezeigt.

#### UC-03: WLAN am Stift konfigurieren
Zur Einrichtung der WLAN-Verbindung stellt der Stift kurzzeitig ein unverschlüsseltes WLAN-Netz bereit (tiptoi_TW...), mit dem sich ein Hilfsgerät verbinden kann. Über die IP-Adresse 192.168.1.1 im Browser werden dem Stift die WLAN-Zugangsdaten übergeben. Der Stift bestätigt die erfolgreiche Verbindung.

#### UC-04: Audiodatei suchen und herunterladen
Der Benutzer gibt in der Suchleiste den Titel des tiptoi-Produkts ein und bestätigt. Bestätigung durch Klick auf das Download-Icon am tiptoi. Der Download startet automatisch vom Ravensburger Server.

#### UC-05: Audiodatei auf Stift übertragen
Die Audiodatei wird automatisch auf den angeschlossenen tiptoi-Stift installiert. Der tiptoi Manager zeigt den Fortschritt an.

#### UC-06: Stift-Inhalte verwalten
In der Navigation unter "Stift und Inhalte verwalten" ist eine Liste Ihrer installierten Produkte. Nicht benötigte Audiodateien können gelöscht werden, um Speicherplatz freizugeben. Der Manager zeigt auch an, ob Aktualisierungen für installierte Produkte verfügbar sind.

#### UC-07: Firmware aktualisieren
Der tiptoi Manager informiert automatisch über verfügbare Firmware-Updates und hilft beim Aktualisieren des Betriebssystems des Stifts. Das Update wird durch den Benutzer heruntergeladen und auf den Stift übertragen. 

### Anwendungsfall tiptoi-Stift

![Anwendungsfalldiagramm tiptoi-Stift](/Anwendungsdiagramm_Stift.png)

### **UC01: Produkt aktivieren und spielen**
Das Kind tippt mit dem tiptoi-Stift auf ein Produkt (z. B. Buch oder Spiel).  
Der Stift liest den gedruckten OID-Code und spielt automatisch die passende Audiodatei ab.  
Das Produkt kann direkt genutzt werden, ohne zusätzliche Einrichtung.

---

### **UC04: Einstellungen anpassen**
Das Kind oder die Eltern verändern direkt am Stift einfache Einstellungen wie Lautstärke, Systemtöne oder LED-Helligkeit.  
Die gewählten Einstellungen werden sofort übernommen und dauerhaft gespeichert.

---

### **UC03: Stift verwalten**
Die Eltern prüfen über das Stiftmenü grundlegende Informationen wie Speicherplatz, verfügbare Inhalte oder den Verbindungsstatus.  
Diese Verwaltungsfunktionen werden vollständig am Gerät ausgeführt, ohne PC oder zusätzliche Software.

---

### **UC05: Stift aufladen**
Die Eltern verbinden den Stift per USB-Kabel oder Netzteil mit einer Stromquelle.  
Der Stift beginnt automat



## Annahmen & Grenzen – Fortlaufendes Log

Dieses Log dokumentiert alle relevanten Annahmen und Systemgrenzen, die während der Modellierung des tiptoi-Projekts getroffen wurden.  
Es umfasst das gesamte System bestehend aus tiptoi Stift, tiptoi Manager (WLAN/USB Edition) und der Content Plattform.


### Logbuch

| Datum       | Typ        | Beschreibung                                                                                         | Begründung / Auswirkung                                                                                     |
|-------------|------------|--------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| 15.10.2025  | Annahme    | Das tiptoi-Projekt umfasst Stift, Manager-Software (WLAN/USB Edition) und Content-Plattform.          | Definiert die Systemgrenze für alle Diagramme und Modelle.                                                  |
| 15.10.2025  | Annahme    | Der Stift kommuniziert über USB oder WLAN mit dem Manager.                                             | Entspricht realer Funktion; vereinfacht die Modellierung.                                                   |
| 15.10.2025  | Grenze     | Bluetooth oder andere Funkverbindungen werden ausgeschlossen.                                          | Reduziert Modellkomplexität; Fokus bleibt auf USB/WLAN.                                                     |
| 20.10.2025  | Annahme    | Die Content-Plattform liefert alle Inhalte (Audiofiles) und Firmware.                                  | Klare Schnittstelle zwischen internem System und externen Services.                                         |
| 20.10.2025  | Grenze     | Technische Details der Content-Plattform werden nicht modelliert.                                      | Fokus liegt auf Architektursicht, nicht Implementierung.                                                    |
| 22.10.2025  | Annahme    | Eltern verwalten Inhalte und Einstellungen; Kinder nutzen den Stift nur produktiv im Spielbetrieb.    | Entspricht realem Nutzungsverhalten.                                                                        |
| 24.10.2025  | Grenze     | Fehlersituationen und Ausnahmen werden nicht im Detail modelliert.                                     | Diagramme bleiben fokussiert auf Standardabläufe.                                                           |
| 30.10.2025  | Annahme    | Der Manager kann mehrere Stifte verwalten, aber nur einen gleichzeitig verbinden.                      | Vereinfachte technische Darstellung; eindeutige Zuordnung im Modell.                                        |
| 05.11.2025  | Grenze     | Hardwareaspekte wie Akku, Speicherchips oder Lautsprecher werden nicht betrachtet.                     | Für Softwarearchitektur nicht relevant.                                                                     |
| 08.11.2025  | Annahme    | Offline-Nutzung ist möglich, sofern Inhalte lokal verfügbar sind.                                      | Beeinflusst Speicherlogik, nicht jedoch Architekturdiagramme.                                               |
| 12.11.2025  | Annahme    | Das Projekt bezieht sich ausschliesslich auf die WLAN-Edition (aktuelle Produktgeneration).            | Verhindert Versionskonflikte; hält Scope eindeutig.                                                         |
| 12.11.2025  | Grenze     | Sicherheit & Datenschutz werden nur konzeptionell berücksichtigt.                                       | Vollständige Analyse erfolgt ausserhalb des Projektumfangs.                                                 |

### Hinweis  
Dieses Log dient der Konsistenz des Gesamtprojekts und bildet Annahmen ab, die **für alle Diagramme und Artefakte gelten**.  
Detailfeedback zu einzelnen Use-Cases wird **nicht** im Log dokumentiert, da es keinen Einfluss auf die Systemgrenzen oder Architekturentscheidungen hat.

# Kontext & Abgrenzung

![Kontextdiagramm_Tiptoi](/kontextdiagramm_tiptoi.png)

Das tiptoi Integrated Learning Environment (ILE) stellt ein vernetztes Lernökosystem der Ravensburger AG dar, das physische Lernprodukte mit digitaler Audio-Interaktion verbindet. Kern des Systems ist der tiptoi Digital Pen, der mittels Optical Identifier Codes (OID) gedruckte Markierungen auf Lernmedien erkennt und kontextabhängige Audioinhalte auslöst. Diese Inhalte werden in proprietären GME-Dateiformaten gespeichert, die strukturierte Metadaten, Audiosequenzen und Interaktionslogik enthalten.

Die TipToi Manager Application auf PC/Mac fungiert als Bindeglied zwischen Benutzer, Gerät und der Ravensburger Plattform zur Inhaltsbereitstellung. Über diese Plattform werden lizenzierte Inhalte, Firmware-Updates und Medienpakete bereitgestellt, während lokale Synchronisations-Services die Offline-Verfügbarkeit sicherstellen. Der Erziehungsberechtigte (Elternkonto) übernimmt dabei Geräteverwaltung, Content-Käufe und Datensynchronisation über WLAN oder USB-Schnittstellen.
	
Das Kontextdiagramm modelliert die Systemgrenze des tiptoi ILE als geschlossene, integrierte Lernarchitektur mit externen Entitäten wie Content-Autoren, Distributionspartnern, pädagogischen Einrichtungen und Supportsystemen. Es zeigt den Datenfluss von der Content-Erstellung über Autorisierung und Distribution bis zur Endnutzung im Lernkontext und verdeutlicht die technische und organisatorische Kopplung zwischen physischem Lernmedium, digitalem Content-Management und Nutzerinteraktion.

Ziel der Darstellung ist eine architektonische Sicht auf das tiptoi-Ökosystem mit Fokus auf Interoperabilität, Datenaustausch und Integrationspunkten innerhalb der digitalen Lerninfrastruktur von Ravensburger.

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


# Verteilungssicht

![Verteilungsdiagramm](/Verteilungsdiagramm.png)

### Zweck und Kontext

Das Verteilungsdiagramm beschreibt die physische und softwaretechnische Architektur des tiptoi-Systems. Es stellt dar, wie die Systemkomponenten auf Geräte und Server verteilt sind und über welche Kommunikationswege digitale Inhalte (Audio, Firmware, Metadaten) bereitgestellt und genutzt werden. Es zeigt eine klare Trennung zwischen Clientgerät, Endgerät, Backend und Content-System. Diese Struktur ermöglicht eine robuste Bereitstellung digitaler Inhalte und unterstützt ein wartbares, skalierbares und überwiegend offline funktionierendes Gesamtsystem.

### Systemübersicht der Systemelemente
**PC / Laptop**

Der PC bzw. Laptop dient als Clientgerät und stellt das Betriebssystem als Ausführungsumgebung für den tiptoi Manager bereit.
Dieser verwaltet den tiptoi-Stift, lädt Inhalts- und Firmwaredateien über HTTPS vom Backend und überträgt sie per USB oder optional WLAN auf den Stift.

** tiptoi-Stift**

Der tiptoi-Stift verwendet eine eingebettete Firmware zur OID-Erkennung, Audioausgabe und lokalen Inhaltsverwaltung. Inhalte werden vom tiptoi Manager übernommen; zusätzlich kann der Stift über HTTPS Status- oder Registrierungsdaten an den Backend-Webservice senden.

**Ravensburger Server**

Der Server bildet das Backend und stellt in einer Webserver-Umgebung den tiptoi Webservice (REST-API) bereit.
Dieser liefert Inhalte und Firmware an den tiptoi Manager und greift auf die Produktdatenbank zu, in der Produkt- und Lizenzdaten verwaltet werden.

**Content Plattform**

Die Content Plattform umfasst das Inhaltsverwaltungssystem sowie die Content-Auslieferung. Sie stellt alle Audio-, Medien- und Firmwaredateien bereit, die der Webservice für Anfragen des Clients benötigt.

**Digitales Papier (OID)**

Das digitale Papier enthält OID-Muster, die vom tiptoi-Stift optisch erkannt werden. Es besitzt keine eigene Software, dient jedoch als physische Schnittstelle für die Offline-Nutzung der Inhalte.

### Kommunikations- und Interaktionsmodell

Der tiptoi Manager lädt Inhalte über den Webservice vom Ravensburger Server, welcher die Daten aus der Content Plattform bezieht. Die übertragenen Inhalte werden anschliessend per USB oder WLAN auf den tiptoi-Stift synchronisiert.
Im Betrieb erkennt der Stift die OID-Codes auf dem digitalen Papier und spielt die lokal gespeicherten Inhalte autonom ab.


# Glossar

| **Begriff** | **Erklärung** |
|-------------|----------------|
| **Aktivierungscode** | Code, der ein tiptoi-Produkt freischaltet. |
| **Akteur** | Eine Person oder ein System, das mit tiptoi interagiert. |
| **Autoren- und Medienerstellungssystem** | System, mit dem Lerninhalte für tiptoi produziert werden. |
| **Bidirektionaler Datenfluss** | Daten, die in beide Richtungen gesendet werden können. |
| **Client-Gerät** | PC oder Laptop, der mit dem tiptoi-Stift verbunden wird. |
| **Content Plattform** | Online-System, das Audio-Dateien, Firmware und Inhalte bereitstellt. |
| **Content-Download** | Das Herunterladen von Audio-Dateien oder Firmware. |
| **Desktop-Anwendung** | Auf dem Computer installierte Software wie der tiptoi Manager. |
| **Device (Gerät)** | Physisches Gerät, auf dem Software läuft (z. B. PC, Stift, Server). |
| **Digitaler Handelsservice (DCS)** | System für digitale Käufe und Lizenzen. |
| **Digitale Inhalte** | Dateien wie Audios, Firmware oder Medien, die der Stift benötigt. |
| **Digitales Papier** | Gedrucktes Lernmaterial mit OID-Codes. |
| **Distributionspartner** | Unternehmen oder Händler, die tiptoi-Produkte vertreiben. |
| **Download-Icon** | Symbol in der Software, über das ein Download gestartet wird. |
| **Elternkonto** | Benutzerkonto für Eltern zur Verwaltung von Käufen, Einstellungen und Inhalten. |
| **Erlernbarkeit** | Beschreibt, wie einfach ein Benutzer das System zum ersten Mal bedienen kann. |
| **Execution Environment** | Software-Umgebung, in der ein Programm ausgeführt wird. |
| **Firmware** | Interne Software des tiptoi-Stifts. |
| **GME-Dateiformat** | Proprietäres Dateiformat, das tiptoi-Audio und Interaktionslogik enthält. |
| **Hilfsgerät** | Gerät wie Smartphone, Tablet oder PC, das zur Einrichtung des Stift-WLANs genutzt wird. |
| **HTTPS** | Verschlüsseltes Protokoll für sicheren Datenaustausch. |
| **Inhaltsverwaltungssystem** | Teil der Plattform, der Inhalte speichert und ausliefert. |
| **Integrationspunkte** | Stellen, an denen verschiedene Systeme miteinander verbunden sind. |
| **Interne Inhalte / lokaler Speicher** | Speicherbereich im Stift, in dem heruntergeladene Dateien abgelegt werden. |
| **IP-Adresse 192.168.1.1** | Lokale Adresse, unter der die WLAN-Einrichtung des Stifts erreichbar ist. |
| **Komponente** | Ein logisches Software-Modul innerhalb der Systemarchitektur. |
| **LED-Anzeige** | Leuchtelement des Stifts zur Anzeige von Lade- oder Systemstatus. |
| **Leistungseffizienz** | Beschreibt, wie schnell und ressourcenschonend das System reagiert. |
| **Metadaten** | Zusatzinformationen zu Audio- oder Inhaltsdateien, z. B. Titel oder OID-Zuordnung. |
| **Modifizierbarkeit** | Beschreibt, wie leicht ein System erweitert oder angepasst werden kann. |
| **Netzwerkinfrastruktur** | Verbindungen und Geräte, die Internetzugang ermöglichen. |
| **OID (Optical Identification)** | Unsichtbare Punktmuster, die vom tiptoi-Stift erkannt werden. |
| **Offline-Nutzung** | Betrieb des Stifts ohne Internet, wenn Inhalte lokal gespeichert sind. |
| **PC App Manager** | Software auf dem PC zur Verwaltung des Stifts (tiptoi Manager). |
| **POS-System** | Kassensystem, das Produktdaten an Ravensburger übermittelt. |
| **Produktdatenbank** | Datenbank mit Produkt- und Lizenzinformationen. |
| **Ravensburger Server** | Online-Dienst für Audio-Dateien, Produktinformationen und Updates. |
| **Stift-Software** | Software im tiptoi-Stift, die alle Funktionen steuert. |
| **Supportsysteme** | Systeme, die technische Unterstützung oder Hilfestellung bieten. |
| **Synchronisations-Services** | Dienste, die Inhalte zwischen PC, Stift und Plattform abgleichen. |
| **System-Grenze** | Grenze zwischen dem tiptoi-System und externen Akteuren oder Systemen. |
| **Telemetrie** | Automatische Übermittlung technischer Stift-Daten. |
| **tiptoi** | Interaktives Lernsystem mit digitalem Stift und Lernmaterialien. |
| **tiptoi Manager** | Desktop-Programm zur Verwaltung des tiptoi-Stifts. |
| **tiptoi Stift** | Elektronischer Stift, der Codes liest und Audios abspielt. |
| **USB-Massenspeicher** | Der Stift erscheint am PC wie ein externer Speicher. |
| **USB-Verbindung** | Kabelverbindung zwischen Stift und PC. |
| **Usability (Benutzbarkeit)** | Wie einfach und intuitiv ein System zu bedienen ist. |
| **Webserver-Umgebung** | Server-System, das Webdienste wie APIs ausführt. |
| **Webservice / REST-API** | Online-Schnittstelle, über die Daten zwischen Stift, Manager und Server übertragen werden. |
| **WLAN-Konfiguration** | Einrichtung einer WLAN-Verbindung auf dem Stift. |
| **WLAN-Edition** | tiptoi-Stift mit integriertem WLAN-Modul. |
| **WLAN-Router** | Gerät, das den Stift mit dem Internet verbindet. |


---

## Quellen

- NielsenNormanGroup: https://www.nngroup.com/articles/usability-101-introduction-to-usability/
- Ravensburger tiptoi Handbuch (Stift 3. Generation mit Aufnahmefunktion und WLAN)
- Ravensburger Serviceportal: service.ravensburger.de/tiptoi
- tiptoi Manager Download-Seite: ravensburger.de/tiptoi-manager
- Wikipedia: de.wikipedia.org/wiki/Tiptoi
