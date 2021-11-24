---
title: Dokument
parent: Template-Erstellung
nav_order: 10
has_children: false
---

## Dokument/Mappe

Die oberste Ebene eines Templates repräsentiert das zu erstellende Exceldokument. Hier können einige Eigenschaften definiert werden, die dann für das ganze Dokument gelten. Einige können nur hier gesetzt werden; andere können auf einer der unteren Ebenen überschrieben werden. So kann z.B. die Spaltenbreite für das ganze Dokument auf `-1` festgelegt werden, später aber für eine bestimmte Spalte die Breite auf `25` gesetzt werden.

Ein minimales Beispieltemplate könnte so aussehen:

```json
{
    "filename": "simple-data-export.xlsx",
    "name": "Tabellenblatt1",
    "columnWidth": -1,
    "rows": [
        {
            "values": ["Last Name", "First Name", "Gender"]
        },
        {
            "values": ["Waldherr", "Nils", "m"]
        }
    ]
}
```

Die wichtigsten Eigenschaften sind:

### filename

Der Dateiname der zu erstellenden Exceldatei. Wird `filename` nicht definiert, dann ist der Dateiname `[Datum]+[Uhrzeit].xlsx`.


### location

Der Ort, an dem die erstellte Exceldatei gespeichert werden soll. Das kann ein Pfad im Dateisystem sein oder Feld in einer Tabelle. Wird `location` nicht definiert, wird die Datei in den Ordner `fx_reports` auf dem Schreibtisch geschrieben.

### name

Name des Arbeitsblattes. Standardwert: sheet[n]


### columns

Liste von Spalten.
Siehe [Column]({% post_url column %})

### rows
Liste von Zeilen.
Siehe [Row]({% post_url row %})


### cells
Liste von Zellen.
Siehe [Cell]({% post_url cell %})


### display

Mit `display` kann man die Anzeigeeigenschaften festlegen, mit denen die Datei nach dem Öffnen angezeigt wird. Zwei Werte können gesetzt werden:

**hideGrid**: boolscher Wert

Gitternetz anzeigen oder ausblenden

**zoom**: Ganzzahl zwischen 25 und 400

Vergrößerung

```json
"display": {
    "hideGrid": true,
    "zoom": 150
}
```

### format


### columnWidth

-1: auto

### print