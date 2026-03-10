# 3. Das Grundprinzip

Im ERV mit der Justiz werden Schriftgutobjekte (Dokumente und Akten) zwischen

- **identifizierten** und
- **authentifizierten** Postfachinhabern auf einem
- **sicheren elektronischen Transportweg**

ausgetauscht.

Sind diese drei Voraussetzungen erfüllt, handelt es sich um einen **sicheren Übermittlungsweg**.

## Automatisierte Weiterverarbeitung

Um die Übernahme in die jeweiligen IT-Systeme der Kommunikationspartner automatisiert zu ermöglichen, werden **strukturierte, maschinenlesbare Daten** beigefügt.

## Technische Standards

Für die drei Grundsäulen wurden technische Standards abgestimmt und die erforderlichen IT-Anwendungen bereitgestellt:

| Säule | Standard / System |
|-------|-------------------|
| Sicherer Transport | EGVP-Transportprofil auf Basis des OSCI-Transportstandards |
| Sichere Identitäten | SAFE-Verzeichnisdienst |
| Automatisierte Weiterverarbeitung | XJustiz |

## Kommunikationsschema

```
ERV-Teilnehmer  ←→  ERV-Teilnehmer

  ↕ XJustiz             ↕ XJustiz
  (automatisierte        (automatisierte
   Weiterverarbeitung)    Weiterverarbeitung)

  ↕ SAFE                 ↕ SAFE
  (sichere Identitäten)  (sichere Identitäten)

  ←———— EGVP (sicherer Transport) ————→
```

Jeder EGVP-Teilnehmer benötigt eine sogenannte **EGVP-Sende- und Empfangskomponente**, um Nachrichten zu versenden und zu empfangen. Einzelheiten sind in den Dokumenten zur Einrichtung von beBPo oder eBO enthalten.
