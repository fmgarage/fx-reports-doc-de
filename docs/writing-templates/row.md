---
title: Zeile
parent: Template-Erstellung
nav_order: 3
has_children: false
---

## Zeile

In einer Zeile können Daten stehen, oder sie ist eine Kopfzeile oder eine Zusammenfassung.

Wenn eine Zeile Daten enthalten soll, gibt es unterschiedliche Arten, diese bereitzustellen: Die Daten können direkt in das Objekt unter `values` geschrieben werden oder man verweist mit `path` auf eine externe Datei oder Felder? >@todo
Bestehen die bereitgestellten Daten aus mehreren Sets, werden auch mehrere Zeilen aus einem `row` Objekt entstehen.
Wenn eine Zeile eine Kopfzeile sein soll, muss `"type": "header"` gesetzt sein.

Bei einer Zusammenfassung ...


```json
"rows": [
    {
        "type": "header",
        "values": [ "Title", "Firstname", "Surname" ],
        "format": "bold"
    },
    {
        "path": "desktop/examples/data-blocks/data-file.xlsx",
        "fields": [ "Title", "GivenName", "Surname" ]
    }
]
```

### type

**header**

Die Zeile ist ein Kopfzeile.

>@todo was macht das? -> Beispiel data-blocks: Header ist nur ein Format?

**data**

Die Zeile enthält Daten.

**summary**

Die Zeile enthält eine Zusammenfassung.

### contentType

Lies Daten als `json`, `csv` oder `tab`

>@todo bezieht sich auf path odervalues?


### values

*Typ* `object` `array`

type: "string", "number", "boolean", "null"

default

Ein Wert oder eine Liste von Werten, die in die Zeile geschrieben werden. Bei einer Liste von Werten können die Werte auch wiederum Listen mit Werten sein, dann werden mehrere Zeilen befüllt.

>@todo besseres Beispiel, bin gerade einfallslos
```json
"values": [
    ["name1", "place1", "group1"],
    ["name2", "place2", "group2"],
    ["name3", "place3", "group3"]
]
```

### path

*Typ* `string`

Pfad zu einer Quelldatei im `xlsx` Format. Kann ein Pfad im Dateisystem oder zu einem (Container)Feld in einer Tabelle sein.

### fields

*Typ* `array`

*abhängig von* `path`

Welche Felder sollen aus der Quelldatei geholt werden. Bezieht sich auf die Kopfzeile, die Werte bezeichnen die Spaltennamen.

```json
"fields": ["field_1", "field_5", "field_6"]
```

### includeFirstRow

*Typ* `bool`

*abhängig von* `path`

*default* `true`

Legt fest, ob die erste Zeile eingeschlossen ist, wenn Daten aus Quelldatei geholt werden. Sollte auf `false` gesetzt werden, wenn die Quelldatei ein Kopfzeile hat, die nicht im Zieldokument auftauchen soll.

```json
"includeFirstRow": true
```

### limit

number of rows from source

### offset

start at row

### pos

### height

int

### widths

array of int

### format

