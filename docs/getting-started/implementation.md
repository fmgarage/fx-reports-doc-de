---
title: Implementierung
has_children: true
parent: Erste Schritte
nav_order: 3
---

## Implementierung

Dieser Artikel beschreibt, wie man FX Reports mit der eigenen Anwendung verknüpft/verbindet



> @todo Vobereitung: beide im selber Ordner, auf dem Server

Es gibt 2 Möglichkeiten, wie man die Elemente in die eigene Lösung integriert:



### 1. Mithilfe des Add-ons

Möglich ab FileMaker 19.  

(Ab hier wird der Leser geduzt)

Den einfachsten Weg, FX Reports in deine Lösung zu implementieren, bietet das Add-on. Lade dir dazu den entsprechenden Ordner aus dem Repository und kopiere ihn den `AddonModules` Ordner.

Es gibt eine unkomplizierte Variante, diesen Ordner zu finden: über die FileMaker Plugin Einstellungen lässt sich das Plugin Verzeichnis öffnen. Ausgehend von dort geht man 2 Schritte höher in der Verzeichnisstruktur und dann hinein in `Extensions`, wo sich `AddonModules` befindet.

> @todo deutsches Wort für Repository

macOS:

`/Users/<User>/Library/Application Support/FileMaker/Extensions/AddonModules/`

Windows:

`C:\Users\<User>\AppData\Local\FileMaker\Extensions\AddonModules\`

> @todo besser vielleicht: Link auf Anleitung im Netz

Dann starte FileMaker Pro neu. Nun kannst du im Layoutmodus in der linken Seitenleiste unter dem Reiter "Add-ons" das Add-on hinzufügen. Mit der `+` Schaltfläche unten öffnet sich das Auswahlfenster, in dem jetzt auch FX_Reports zur Auswahl steht. Wähle "FX_Reports" aus und klicke auf "Auswahl". Die Elemente, die nötig sind, um FX Reports anzusprechen, sind jetzt verfügbar.

(Ab hier wieder neutrale Ansprache)

Das Add-on ersetzt nicht die FX_Reports-Datenbank, sondern stellt nur die Verbindung her bzw. vereinfacht die Implementierung in die eigene Lösung.

### 2. Manuell per copy/paste

Die Datei `FX_ReportsExample.fmp12` dient als Vorlage und beinhaltet die Elemente, die für die Integration nötig sind.

Die Elemente müssen in dieser Reihenfolge in die eigene Lösung kopiert (oder angelegt) werden:

#### Tabelle: FxReports

Zuerst wird die Tabelle `FxReports` in die Zieldatei kopiert.

> @todo Repräsentanz anlegen, nicht Tabelle kopieren, näher beschreiben

#### Custom Functions:

Dann werden die Custom Functions kopiert:

`SError.catch_v7`

`SError.display_v6`

#### Scripts

Zuletzt werden die Scripte aus dem `FxReports` Ordner unter `# Connector` kopiert:

`*FxReports.excelGenerate( $filename, $location )`

`*FxReports.excelValidate()` (optional)

## Grundsätzliches zum Vorgehen

Die Tabellenrepräsentanz `FxReports` darf nicht umbenannt werden.

- Einen Excel Export aus der eigenen Anwendung exportieren, z.B. nach tmp

- Diesen Dateipfad im Template in `path` als Quelle angeben

- Vorbereitete Templates z.B. in Feld(ern) der eigenen Lösung speichern

- Templates ggf. für Ausgaben anpassen, z.B. Zieldateiname oder location im json ändern/setzen

- Das Template JSON wird dann in `FxReports::a_container_` kopiert

- Dann wird `*FxReports.excelGenerate( $filename, $location )` aufgerufen.

- Die generierte Datei wird dann am mit `location` und `filename` definierten Ort gespeichert
