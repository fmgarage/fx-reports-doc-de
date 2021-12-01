---
title: Implementierung
has_children: true
parent: Erste Schritte
nav_order: 3
---

## Implementierung / Verwendung der API
> @todo

Dieser Artikel beschreibt, wie man FX Reports mit der eigenen Anwendung verknüpft/verbindet

> @todo Vobereitung: beide im selben Ordner oder auf dem Server

Es gibt 2 Möglichkeiten, wie man die Elemente in die eigene Lösung integriert:

### 1. Mithilfe des Add-ons

Möglich ab FileMaker 19.

Den einfachsten Weg, FX Reports in deiner Lösung zu implementieren/deine Lösung zu integrieren, bietet das Add-on. Lade dir dazu den entsprechenden Ordner aus dem Repository und kopiere ihn den `AddonModules` Ordner.

Es gibt eine unkomplizierte Variante, diesen Ordner zu finden: über die FileMaker Plugin Einstellungen lässt sich das Plugin Verzeichnis öffnen. Ausgehend von dort geht man 2 Schritte höher in der Verzeichnisstruktur und dann hinein in `Extensions`, wo sich `AddonModules` befindet.

> @todo deutsches Wort für Repository

macOS:

`/Users/<User>/Library/Application Support/FileMaker/Extensions/AddonModules/`

Windows:

`C:\Users\<User>\AppData\Local\FileMaker\Extensions\AddonModules\`

> @todo besser vielleicht: Link auf Anleitung im Netz

Falls FileMaker Pro beim Kopieren des Add-ons lief, starte die Anwendung jetzt neu. Nun kannst du im Layoutmodus in der linken Seitenleiste unter dem Reiter "Add-ons" das Add-on hinzufügen. Mit der `+` Schaltfläche unten öffnet sich das Auswahlfenster, in dem jetzt auch FX_Reports zur Auswahl steht. Wähle "FX_Reports" aus und klicke auf "Auswahl". Die Elemente, die nötig sind, um FX Reports anzusprechen, sind jetzt verfügbar.

Das Add-on ersetzt nicht die FX_Reports-Datenbank, sondern stellt nur die Verbindung her bzw. vereinfacht die Implementierung in die eigene Lösung.

### 2. Manuell per copy/paste

Die Zieldatei, `FX_Reports.fmp12` und `FX_ReportsExample.fmp12` müssen im selben Verzeichnis (oder auf dem Server) liegen.

Die Datei `FX_ReportsExample.fmp12` dient als Vorlage und beinhaltet die Elemente, die für die Integration nötig sind.

Die Elemente müssen in dieser Reihenfolge in die eigene Lösung kopiert (oder angelegt) werden:

#### Custom Functions:

Zuerst werden die Custom Functions kopiert:

`SError.catch_v7`

`SError.display_v6`

#### Scripts

Dann werden die Scripte aus dem `FxReports` Ordner unter `# Connector` kopiert:

`*FxReports.excelGenerate( $filename, $location )`

`*FxReports.excelValidate()` (optional)

Die Dateireferenz auf `FX_Reports.fmp12` sollte jetzt vorhanden sein.

#### Tabelle: FxReports

Zuletzt wird die Tabellenrepräsentanz `FxReports` in der Zieldatei angelegt. Sie darf nicht umbenannt werden.

> @todo Repräsentanz anlegen, nicht Tabelle kopieren, näher beschreiben

## Grundsätzliches zum Vorgehen

1. Die **Ausgangsdatei** zur Verfügung stellen

    Als Ausgangsdaten werden üblicherweise die Exporte der eigenen Anwendung genutzt. Diese können in einem beliebigen Verzeichnis, z.B. dem temporären Verzeichnis, platziert werden; oder man legt sie in einem Containerfeld ab.

    Den Pfad zur Quelldatei gibt man dann im Template in `path` als Quelle an.

2. Das **Template** vorbereiten

    Die vorbereiteten Templates können z.B. in Feldern der eigenen Lösung gespeichert werden. Dort kann man sie auch für einzelne Ausgaben anpassen, wie etwa einen bestimmten Zieldateinamen oder den Zielordner setzen.

3. Das **Dokument** mit FX_Reports generieren

    Für die Ausgabe wird:
   - das Template JSON in das Containerfeld `FxReports::a_container_` kopiert
   - das Script `*FxReports.excelGenerate( $filename, $location )` aufgerufen

    Die Datei wird dann generiert und am mit `location` und `filename` definierten Ort (oder per default auf dem Schreibtisch) gespeichert.
