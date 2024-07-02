# Javalin Pdf Server

Webserver mit TLS 1.3, Web-UI und Autorisierung.

## Funktionen

- PDF mit Passwort verschlüsseln
- PDF über selbstsigniertem Zertifikat signieren
- PDF über den Zeitstempeldienst des DFN-Verein (Deutschen Forschungsnetzes) signieren
- PDF mit Passwort verschlüsseln und signieren

## Eingabe über Web-UI

Eine PDF-Datei.

## Ausgabe

Eine modifizierte PDF-Datei.

## Autorisierung

Access-Token zum Setzen eines Cookie-Token.

Cookie-Token erlaubt Nutzung der Web-UI als auch API.

## PDF kompatibel mit gängigen PDF-Viewern

Die Signatur und oder Verschlüsselung folgt dem PDF-Standard.

## Bibliotheken

| Bibliothek            | Autor                                | Lizenz     | Beschreibung                                                 |
| --------------------- | ------------------------------------ | ---------- | ------------------------------------------------------------ |
| slf4j-simple          | Ceki Gulcu                           | MIT        | Ein einfacher SLF4J-Binding, der alle Ereignisse an System.err ausgibt und nur Nachrichten ab INFO-Level druckt. |
| javalin               | David Åse et al.                     | Apache-2.0 | Ein leichtgewichtiges Web-Framework für Kotlin und Java, das auf Jetty basiert. |
| bcprov-jdk18on        | The Legion of the Bouncy Castle Inc. | MIT        | Bietet grundlegende kryptografische Funktionen für Java-Anwendungen. |
| bcpkix-jdk18on        | The Legion of the Bouncy Castle Inc. | MIT        | Erweiterung der bcprov-Bibliothek mit Unterstützung für PKIX, Zertifikatsverwaltung und mehr. |
| itextpdf              | iText Group NV                       | AGPL-3.0   | Eine Bibliothek zur Erstellung und Bearbeitung von PDF-Dokumenten. |
| itext-core            | iText Group NV                       | AGPL-3.0   | Kernkomponenten der iText PDF-Bibliothek.                    |
| itext-pdfa            | iText Group NV                       | AGPL-3.0   | Erweiterung der iText-Bibliothek zur Unterstützung des PDF/A-Standards. |
| commons               | iText Group NV                       | AGPL-3.0   | Gemeinsame Bibliotheken und Hilfsprogramme für die iText-Bibliothek. |
| sign                  | iText Group NV                       | AGPL-3.0   | Komponenten zur digitalen Signatur von PDF-Dokumenten.       |
| bouncy-castle-adapter | iText Group NV                       | AGPL-3.0   | Adapter, der die Bouncy Castle-Kryptobibliothek mit iText integriert. |

## License

Copyright (c) Georg Schmidt 2005-2024

All rights reserved

The text, software and all associated files are the exclusive property of the author and are provided solely for viewing purposes. Any use, copying, modification, distribution, or any other form of utilization is strictly prohibited. No rights are granted to the user, and any unauthorized use is subject to legal action.