┌─────────────────────────────────────────────────────────┐
│ Anwendungsfälle: tiptoi Manager WLAN Edition            │
└─────────────────────────────────────────────────────────┘

UC-01: Produkt aktivieren und spielen
─────────────────────────────────────
Primärer Akteur:      Kind
Sekundäre Akteure:    tiptoi-Stift, tiptoi-Produkt (Buch/Spiel)
Vorbedingung:         - Audiodatei ist auf Stift geladen
                      - Stift ist eingeschaltet
Beschreibung:         Das Kind tippt mit dem tiptoi-Stift auf 
                      das Anmeldezeichen (grünes Power-Button-Symbol) 
                      auf der ersten Doppelseite des tiptoi-Produkts. 
                      Der Stift liest den OID-Code aus dem Produkt 
                      und spielt die entsprechende Audiodatei ab.
Nachbedingung:        Audiodatei wird abgespielt
Quelle:               tiptoi Handbuch, S. 5-6


UC-02: Stift mit PC verbinden und erkennen (via USB)
────────────────────────────────────────────────────
Primärer Akteur:      Eltern
Sekundäre Akteure:    tiptoi-Stift
Vorbedingung:         - tiptoi Manager ist installiert
                      - Stift ist eingeschaltet
Beschreibung:         Verbinden Sie den eingeschalteten tiptoi-Stift 
                      mit Ihrem Rechner. Der tiptoi-Stift wird von 
                      der Software automatisch erkannt und als 
                      USB-Massenspeicher angezeigt.
Nachbedingung:        Stift ist im Manager sichtbar
Quelle:               tiptoi Manager Anleitung


UC-03: WLAN am Stift konfigurieren
──────────────────────────────────
Primärer Akteur:      Eltern
Sekundäre Akteure:    tiptoi-Stift, WLAN-Router
Vorbedingung:         - Stift ist eingeschaltet
                      - WLAN-Zugangsdaten sind bekannt
Beschreibung:         Zur Einrichtung der WLAN-Verbindung stellt 
                      der Stift kurzzeitig ein unverschlüsseltes 
                      WLAN-Netz bereit (tiptoi_TW...), mit dem sich 
                      ein Hilfsgerät verbinden kann. Über die 
                      IP-Adresse 192.168.1.1 werden dem Stift die 
                      WLAN-Zugangsdaten übergeben.
Nachbedingung:        Stift ist mit WLAN verbunden
Quelle:               Service-Portal Ravensburger


UC-04: Audiodatei suchen und herunterladen
──────────────────────────────────────────
Primärer Akteur:      Eltern
Sekundäre Akteure:    Ravensburger Server
Vorbedingung:         - tiptoi Manager ist geöffnet
                      - Internetverbindung besteht
Beschreibung:         Geben Sie in die Suchleiste den Titel Ihres 
                      tiptoi-Produkts ein und bestätigen Sie die Suche. 
                      Klicken Sie auf das Download-Icon an Ihrem 
                      tiptoi-Produkt. Der Download startet automatisch.
Nachbedingung:        Audiodatei ist heruntergeladen
Quelle:               ravensburger.de/tiptoi-manager


UC-05: Audiodatei auf Stift übertragen
──────────────────────────────────────
Primärer Akteur:      Eltern
Sekundäre Akteure:    tiptoi-Stift
Vorbedingung:         - Stift ist per USB verbunden
                      - Audiodatei ist heruntergeladen
Beschreibung:         Die Audiodatei wird automatisch auf den 
                      angeschlossenen tiptoi-Stift installiert.
Nachbedingung:        Audiodatei ist auf Stift verfügbar
Alternativer Ablauf:  Audiodatei kann auch per WLAN übertragen werden
Quelle:               tiptoi Manager Anleitung


UC-06: Stift-Inhalte verwalten
──────────────────────────────
Primärer Akteur:      Eltern
Sekundäre Akteure:    tiptoi-Stift
Vorbedingung:         - Stift ist verbunden
                      - tiptoi Manager ist geöffnet
Beschreibung:         In der Navigation unter "Stift und Inhalte 
                      verwalten" finden Sie eine Liste Ihrer 
                      installierten Produkte. Nicht benötigte 
                      Dateien können gelöscht werden.
Nachbedingung:        Stift-Speicher ist verwaltet
Quelle:               tiptoi Manager Anleitung


UC-07: Firmware aktualisieren
─────────────────────────────
Primärer Akteur:      Eltern
Sekundäre Akteure:    tiptoi-Stift, Ravensburger Server
Vorbedingung:         - Stift ist verbunden
                      - Neue Firmware ist verfügbar
Beschreibung:         Der tiptoi Manager informiert über verfügbare 
                      Firmware-Updates und hilft beim Aktualisieren 
                      des Betriebssystems des Stifts.
Nachbedingung:        Stift hat aktuelle Firmware
Quelle:               tiptoi Manager Anleitung


UC-08: Stift mit Energie versorgen / aufladen
─────────────────────────────────────────────
Primärer Akteur:      Eltern
Sekundärer Akteur:    tiptoi-Stift
Vorbedingung:         - Micro-USB-Kabel ist vorhanden
Beschreibung:         Der Akku des Stiftes kann mit dem mitgelieferten 
                      Micro-USB-Kabel an einem Computer oder einem 
                      USB-Netzteil (500mA-1A, 5V) aufgeladen werden.
Nachbedingung:        Stift ist aufgeladen
Hinweis:              Dieser Vorgang benötigt die tiptoi Manager 
                      Software nicht und ist daher außerhalb der 
                      System-Grenze.
Quelle:               tiptoi Handbuch


UC-09: tiptoi Manager installieren
──────────────────────────────────
Primärer Akteur:      Eltern
System:               Betriebssystem (PC/Mac)
Vorbedingung:         - Installationsdatei ist heruntergeladen
                      - PC/Mac erfüllt Systemanforderungen
Beschreibung:         Die Installationsdatei für den tiptoi Manager 
                      wird auf dem PC oder Mac installiert.
Nachbedingung:        tiptoi Manager ist einsatzbereit
Hinweis:              Dies ist ein Vorbereitungsschritt und kein 
                      Use Case der tiptoi Manager Software selbst, 
                      daher außerhalb der System-Grenze.
Quelle:               ravensburger.de/tiptoi-manager