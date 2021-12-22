---
title: Spalte
parent: Template-Erstellung
nav_order: 2
has_children: false
---

## Spalte

In einem `column` Objekt werden u.a. Breite, Position und Format einer Spalte festgelegt. Außerdem ist es möglich, den Typ (Header, Data, Summary) und den Datentyp zu definieren.
Als Header wird eine Spalte zum Beispiel benutzt, wenn sie die y-Achsenbeschriftung beinhaltet.

```json
{
    "type": "data",
    "dataType": "number",
    "format": {
        "bold": true
    }
}
```

### type

**header**

**data**

**summary**

### dataType

"text", "number", "date", "timestamp"

### width


### pos

Position der Spalte von links, beginnend mit 0. Wird entweder als einzelne Zahl angegeben – 

3

Oder wenn ein Bereich definiert werden soll als Array, wobei die erste Zahl die erste Spalte des Bereichs angibt und die zweite die Länge.

[2,5] 

### format
link

