---
layout: page
title: 3 – Das Grundprinzip
nav_order: 3
---

# Das Grundprinzip

Im ERV mit der Justiz werden Schriftgutobjekte (Dokumente und Akten) zwischen:

- **identifizierten** und
- **authentifizierten** Postfachinhabern auf einem
- **sicheren elektronischen Transportweg**

ausgetauscht.

Sind diese drei Voraussetzungen erfüllt, handelt es sich um einen **sicheren Übermittlungsweg**.

## Strukturierte Daten

Um die Übernahme in die jeweiligen IT-Systeme der Kommunikationspartner automatisiert zu ermöglichen, werden **strukturierte, maschinenlesbare Daten** (im XJustiz-Format) beigefügt.

## Drei technische Säulen

Für die drei Grundsäulen wurden technische Standards abgestimmt und IT-Anwendungen bereitgestellt:

| Säule | Standard / System | Funktion |
|-------|-------------------|----------|
| Sicherer Transport | **EGVP** (OSCI-Transportstandard) | Verschlüsselte Übertragung der Nachrichten |
| Sichere Identitäten | **SAFE** (Verzeichnisdienst) | Identifizierung der Postfachinhaber |
| Automatisierte Weiterverarbeitung | **XJustiz** | Strukturierte maschinenlesbare Daten |

## Zusammenspiel

```
ERV-Teilnehmer                              ERV-Teilnehmer
     │                                           │
     ├── Automatisierte                           ├── Automatisierte
     │   Weiterverarbeitung (XJustiz)             │   Weiterverarbeitung (XJustiz)
     │                                           │
     ├── Sichere Identitäten (SAFE) ◄────────► Sichere Identitäten (SAFE)
     │                                           │
     └── Sicherer Transport (EGVP) ◄─────────► Sicherer Transport (EGVP)
```
