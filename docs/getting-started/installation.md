---
title: Installation
has_children: true
parent: Erste Schritte
nav_order: 1
---

## Installation

### Systemvoraussetzungen

- Eine Installation von FileMaker Pro / Server? ab der Version 18.
- MBS-Plugin ab Version 10.0
- LibXL ab Version (xxx)

### MBS-Plugin installieren

FX_Reports benötigt das MBS-Plugin. Zum Ausprobieren wird keine Lizenz benötigt, die Demoversion des Plugins ist fast uneingeschränkt nutzbar. Download und Infos zu Lizenzen gibt es bei [Monkeybread Software](https://www.monkeybreadsoftware.com/filemaker/buy/).

Hier gibt es die einzelnen Downloads:

|Version|Link|Plugindatei|
|-|-|-|
| macOS | https://fmgarage.com/download/plugins/mbs/mbs-mac.zip | MBS.fmplugin |
| Windows 64bit | https://fmgarage.com/download/plugins/mbs/mbs-win64.zip | MBS.fmx64 |
| Windows 32bit | https://fmgarage.com/download/plugins/mbs/mbs-win32.zip | MBS.fmx |
| Linux | https://fmgarage.com/download/plugins/mbs/mbs-linux.zip | MBS.xxx.fmx |

Die Plugindatei muss in das FileMaker Plugin Verzeichnis kopiert werden. Je nach Betriebssystem gibt es eine passende Datei.

Falls noch keine Plugins installiert wurden, existiert das Verzeichnis noch nicht. Es wird aber angelegt, wenn man über die FileMaker Einstellungen zu Plugins geht und auf 'Plugin-Ordner anzeigen' klickt. Dann öffnet sich das Verzeichnis und man legt die Plugindatei hinein.

Nachdem FileMaker neu gestartet wurde, wird das Plugin im Plugin Reiter in den Einstellungen angezeigt. Es ist nun einsatzbereit.

### LibXL installieren

Download:

|Version|Link|Plugindatei|
|-|-|-|
| macOS | https://fmgarage.com/download/plugins/libxl/libxl-mac.zip | libxl.dylib |
| Windows 64bit | https://fmgarage.com/download/plugins/libxl/libxl-win64.zip | libxl.dll |
| Windows 32bit | https://fmgarage.com/download/plugins/libxl/libxl-32.zip | libxl32.dll |
| Linux | https://fmgarage.com/download/plugins/libxl/libxl-linux.zip | libxl<area>.so |

Für die Erstellung von Excel-Dokumenten wird die Erweiterung LibXL ab Version (xxx) benötigt. Die Bibliothek wird über das MBS-Plugin angesprochen.

Wie auch das MBS-Plugin wird die LibXL Datei in das Plugin Verzeichnis von Filemaker kopiert.

### FX_Reports öffnen/installieren(?)

Die Datei FX_Reports.fmp12 darf nicht umbenannt werden. Man kann sie lokal öffnen oder auf den Server laden.

### Hosting mit FileMaker Server

Es wird eine entsprechende Lizenz[link_zur_lizenz] benötigt, mit der Demo funktioniert das Hosting nicht.

### schon manuell nutzbar/testen/ausprobieren
