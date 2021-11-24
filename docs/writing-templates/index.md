---
title: Template-Erstellung
nav_order: 30
has_children: true
---

## Was ist ein Template?

Ein Template definiert das zu erstellende Excel Dokument. Es beschreibt, wie es aussieht und welche Daten an welcher Stelle stehen. Das Template ist zwingend notwendig/unabdingbar, um mit FX Reports Excelausgaben zu erstellen. Wenn man nicht gleich ein eigenes Template "from scratch" erstellen will, ist es eine gute Idee, ein vorhandenes zu nehmen und anzupassen.

Als Blaupause/Vorlage/Bauanleitung braucht ein Template ein valides **JSON Schema**. Darin sind die erlaubten Werte und Strukturen zum Bauen eines Templates definiert. Zum Beispiel wird darin festgelegt, an welcher Stelle man Spalten und Zellen schreiben kann oder welche Schlüssel und Werte in einem Format definiert werden dürfen. Das Schema für FX Reports haben wir in `https://fmgarage.com/schemas/json2excel/v2-1-0.json`@todo definiert.



## Template-Erstellung > Bearbeitung/Werkzeuge?

Templates werden als JSON Dokumente geschrieben. Die Syntax bzw. das Schema ist leicht zu erlernen. Eine gute Möglichkeit, die Funktionen kennenzulernen, sind die Beispiele (Ordner `examples`) aus dem FX_Reports Verzeichnis.

> grundsätzlich kann man jeden Text-Editor verwenden.

### mit dem Online-Editor

Unser [Online-Template-Editor](https://fmgarage.github.io/fx-reports/editor/) bietet eine komfortable Möglichkeit, Templates in einer grafischen Oberfläche erstellen.

> Tipp: einfach mal ein Example pasten und "update form" drücken

### mit VSCode

In VSCode kann ein Schema für bestimmte Dateien und/oder Ordner hinterlegt werden. Das heißt, wir können hier auch unser json2excel Schema für Template Dateien eintragen. Entweder überlegt man sich einen Suffix für alle Template Dateien oder öffnet alle Dateien mit der Endung `json` in einem bestimmten Ordner mit diesem Template.

#### VSCode einrichten

Das wird in der Konfigurationsdatei `settings.json` gemacht. Es gibt 2 Wege, diese zu öffnen:

1. mit der Maus
- Settings UI öffnen mit <kbd>⌘ Command</kbd> + <kbd>,</kbd> / <kbd>Strg</kbd> + <kbd>,</kbd> oder über das Appmenu
- unter `Erweiterungen/JSON/JSON: Schemas` klicken auf `In "settings.json" bearbeiten`
- die Datei öffnet sich

2. mit Tastaturkommandos
- settings.json direkt öffnen mit <kbd>⌘ Command</kbd> + <kbd>⇧ Shift</kbd> + <kbd>P</kbd> / <kbd>Strg</kbd> + <kbd>⇧ Shift</kbd> + <kbd>P</kbd>
- im Suchfeld suchen nach `Open Settings (JSON)`
- die Datei öffnet sich

Innerhalb der äussersten geschwungenen Klammern, an letzter Stelle (Komma ans Ende des vorherigen Eintrags, weil jetzt ein neuer kommt), folgenden Eintrag hinzufügen:

```json
"json.schemas": [
    {
        "fileMatch": [
            "examples/**/*fxrpxl.json",
            "custom/**/*fxrpxl.json"
        ],
        "url": "./schema/fxrp_excel_v2.schema.json"
    }
]
```
> @todo welches beispiel?
```json
"json.schemas": [
    {
        "fileMatch": [
            "**.prefix.json"
        ],
        "url": "https://raw.githubusercontent.com/fmgarage/fx-reports/main/schema/excel_v2-1.schema.json"
    }
]
```

Unter `fileMatch` den Dateinamen und bei Bedarf den Pfad benennen, bei der das Schema genutzt werden soll. Die Namensmaske ist frei bestimmbar. Dann die `settings.json` speichern.

Wird nun eine entsprechende Datei bearbeitet, werden die möglichen Werte innerhalb der Anführungszeichen angezeigt.

### Testen eines Templates

Das Template in FX Reports in den Editor kopieren und mit dem Button `Generate xlsx` ein Excel Dokument erzeugen und prüfen.



## Aufbau eines Templates

> basic Aufbau

**Mappe/Dokument:**

In der obersten Ebene des JSON-Dokuments werden die dokumentspezifischen Eigenschaften definiert, wie z.B. der Ausgabeort und Dateiname des Exceldokuments und für das ganze Dokument gültige Format-, Anzeige- und Druckoptionen.



**Arbeitsblatt:**

Dann folgen Eigenschaften des Arbeitsblattes. Das können auch wieder Formatoptionen sein, fixierte Bereiche oder z.B. die standard@todo Spaltendefinitionen. Außerdem werden hier die Spalten, Zeilen und Zellen des Arbeitsblattes definiert.



**Spalten:**

Hier werden Format- und Dateneigenschaften eingestellt. Dazu gehören u.a. die Spaltenbreite und Position. 



**Zeilen:**

Hier können sowohl Kopf- als auch Datenzeilen und Auswertungen definiert werden. Daten können als individuelle Zeilen oder als Referenz auf eine Datenquelle im Template gespeichert werden. Zeilenspezifische Formatoptionen werden hier ebenfalls festgelegt. 



**Zellen:**

Für einzelne Zellen kann über ihre Position Größe, Format oder auch Inhalt, also Daten oder etwa eine Bilddatei (z.B. für Logos), festgelegt werden. So können auch aufwändig gestaltete Dokumente mit Überschriften, Beschreibungstexten oder Logos umgesetzt werden. 




## Wir erstellen ein Beispieltemplate

```json
{
    "filename": "report.xlsx",
    "columnWidth": -1
}
```

Wir beginnen mit einem neuen Template und legen den Namen des zu erstellenden `xlsx` Dokuments fest und setzen die Spaltenbreite `columnWidth` mit `-1` auf automatisch.

Nun wollen wir die Daten, die in der Tabelle stehen sollen, festlegen. Aus einer Exportdatei mit vielen Spalten wählen wir die 3 Spalten `data_name`, `data_age`, `data_adress`, die in der Tabelle als `Name`, `Alter`, `Wohnort` erscheinen sollen. Wir fügen den Knoten `rows` zur Mappe/zum Dokument hinzu und legen darin eine Liste (Liste okay oder immer Array?)@todo mit 2 `row` Objekten an. Die erste Zeile soll vom Typ `header` sein und fett formatiert werden. Die Werte für die Zellen liefern wir wiederum als Liste von `values`: "Name", "Alter", "Wohnort".

(Arrays Reiehnfolge bleibt immer bestehen)

Und im Formatknoten legen wir mit `"bold": true` eine Formatierung für die Zeile fest.

Im zweiten Objekt holen wir aus der Exporttabelle `data-file.xlsx` im Tempverzeichnis die Daten 3 bestimmten Spalten. In den Knoten `path` schreiben wir also den Pfad zur Quelldatei und unter `fields` listen wir die Spalten, die extrahiert werden.

> *INFO* Spalten wählen mit `fields` funktioniert nur mit einer entsprechend beschrifteten Kopfzeile. Wenn keine Kopfzeile existiert, kann es sich lohnen, eine einzufügen und mit eindeutigen Benennungenzu versehen. Sollte die Beschriftung auf der y-Achse stehen ... Sollten die Daten horizontal orientiert ...

Weil die Daten aus der Quelltabelle mehrere Zeilen umfassen, entstehen aus diesem Objekt in `rows` auch entsprechend mehrere Zeilen in der Ausgabetabelle.

Der `rows` Eintrag sieht nun so aus:

```json
    "rows": [
        {
            "type": "header",
            "values": ["Name", "Alter", "Wohnort"],
            "format": {"bold": true}
        },
        {
            "path": "tmp/data-file.xlsx",
            "fields": ["data_name", "data_age", "data_adress"]
        }
    ]
```
Als nächstes wollen wir die 3 Spalten naäher definieren. Wir sagen, daß alle 3 Spalten Daten enthalten und daß die zweite Spalte Zahlen beinhaltet. Dazu öffnen wir einen neuen Knoten `columns`. In diesem Knoten stehen in einer sortierten Liste `column` Objekte, die die Spalten von links nach rechts beschreiben.

```json
    "columns": [
        {"type": "data", "dataType": "text"},
        {"type": "data", "dataType": "number"},
        {"type": "data", "dataType": "text"}
    ]
```

Die erste und dritte Spalte setzen allerdings nur die Standardwerte, können also auch weggelassen werden. So müssen wir nur die zweite Spalte definieren, dann aber mit Position `pos`, weil die Position sich nicht mehr aus der Reihenfolge der Einträge ableiten lässt.

Gekürzt um diese Einträge, nur die zweite Spalte:

```json
    "columns": [{"type": "data", "dataType": "number", "pos": 2}]
```

Unser Template sieht nun so aus:

```json
{
    "filename": "report.xlsx",
    "columnWidth": -1,
    "rows": [
        {
            "type": "header",
            "values": ["Name", "Alter", "Wohnort"],
            "format": {"bold": true}
        },
        {
            "path": "tmp/data-file.xlsx",
            "fields": ["data_name", "data_age", "data_adress"]
        }
    ],
    "columns": [{"type": "data", "dataType": "number", "pos": 2}]
}
```
Was haben wir bis jetzt erreicht? Wir haben:
- aus einem vollen Export eine Auswahl von Felder/Spalten in ein neues Exceldokument übertragen
- die Kopfzeile mit lesbaren Werten befüllt und
- den Datentyp für eine Spalte mit Zahlen auf den passenden Wert gesetzt.

> @todo nächste Funktionen
Format und bedingte Formatierung?


---
> @todo Arrays Sortierung bleibt, Objekte sind unsortiert.

### document

### sheet
### columns
### rows
### cells

### definitions: pictures
### definitions: formats
### definitions: fonts




### Paths

- file paths
- container fields
- dynamic paths (tmp, desktop)



### Position

- for row, column, cell
- implicit vs. explicit
- ranges

### Type

- data, header, 



