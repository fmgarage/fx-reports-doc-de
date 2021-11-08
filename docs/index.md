---
title: Start
nav_order: 1
---

## Willkommen zu FX Reports

**FX Reports** ist eine extrem leistungsfähige Erweiterung zur Erstellung von Exporten bei fast alle Funktionen von Excel unterstützt werden, also z.B. Farben, Formate, Bilder und so weiter. Dazu ist **FM Reports** kinderleicht zu integrieren und die Templates für die Ausgabeformate sind einfache JSON-Dokumente.



### Was kann ich damit machen?

Exporte aus FileMaker sind schnell eingerichtet, aber extrem limitiert, nicht nur, was die Formatierung angeht. Das fängt bei den Spaltenüberschriften an, die automatisch von den Tabellen- und Feldnamen übernommen werden. An anderen Ende des Spektrums gibt es das [MBS-Plugin](https://www.mbsplugins.eu/component_XL.shtml) und die [LibXL](https://www.libxl.com)-Erweiterung, mit denen man jede erdenkliche Exceldatei erstellen und mit allen Details, Zelle für Zelle, definieren kann – bzw. auch muss. Das ist in der Regel äußerst mühsam und erfordert eine Menge Programmierarbeit bei der Erstellung eines Ausgabeformats. 

Hier setzt **FX Reports** an und vereint Einfachheit und Flexibilität in einem Tool: Als ein sogenannter Wrapper für die Excel-Funktionen des MBS-Plugins kann der gesamte Funktionsumfang unterstützt werden, die Definition erfolgt mithilfe Text in Form von JSON, getreu dem Motto: *“Simple things should be simple, complex things should be possible”* (Alan Kay).

Ein kleines Beispiel: Das Austauschen der Spaltenüberschriften in einer Exportdatei geht so:

```json
{ "rows": [
    {"values": [ "First Name", "Last Name", "Age" ]},
    {"path": "desktop/contacts.xlsx"}
]}
```



Ein großer Vorteil von **FX Reports** liegt darin, dass neue Exportformate oder Änderungen an bestehenden nicht mehr programmiert werden müssen, es reicht die Bereitstellung eines Textes. 



Ein Großteil der Excel-Funktionalität wird in der aktuellen Version bereits unterstützt, unter anderem:

- mehrere Arbeitsblätter
- Formatierung von Text, Zahlen, Datum und Zeit
- Bilder (z.B. Logos oder Icons)

**FX Reports** wird von uns kontinuiertlich verbessert und der Funktionsumfang erweitert. Wenn du eine Idee oder einen Verbesserungsvorschlag hast, schreib einfach ein [Issue](https://github.com/fmgarage/fx-reports/labels/enhancement) oder starte eine [Diskussion](https://github.com/fmgarage/fx-reports/discussions) (in English please!). 

### What's in the Pipeline?

#### Formats

Integration into your existing solution will be even easier with formats.

This will also include support for native outputs

#### Queries

#### DynaPDF

Using a JSON schema as a meta format for describing and generating complex PDF documents using a similar approach like for Excel.

#### Word






### Support or Contact

Having trouble with implementing FX_Reports? Not sure, if FX_Reports matches your individual requirements? We are happy to assist, just contact us via our website, Twitter ([@fmgarage](https://twitter.com/fmgarage)) or email (support@fmgarage.com). 
