---
layout: page
title: 7 – XJustiz
nav_order: 7
---

# XJustiz

Dank der maschinenlesbaren strukturierten Daten im XJustiz-Format können Nachrichteninhalte **automatisiert** an die richtigen IT-Systeme ausgesteuert oder an den richtigen Bearbeiter weitergeleitet werden. XJustiz ermöglicht die automatisierte Übernahme von Daten in die IT-Systeme der Empfänger.

- Herausgegeben von der **Bund-Länder-Kommission (BLK)** für Informationstechnik in der Justiz
- Frei verfügbar auf [www.xjustiz.de](https://www.xjustiz.de)
- **Jährlicher Releasezyklus** – neue Version löst die vorherige ab
- Neue Versionen werden 12 Monate vor Gültigkeit veröffentlicht

## Aufbau einer XJustiz-Nachricht

Die XJustiz-Nachricht trägt immer den Dateinamen **`xjustiz_nachricht.xml`**.

Für die verschiedenen fachlichen Kommunikationsanlässe sind XJustiz-Nachrichten vorgesehen. Es wird unterschieden zwischen:

- **Basisnachricht** – fachübergreifend
- **Übermittlung Schriftgutobjekte** – fachübergreifend
- **Fachnachrichten** – für spezielle Fachbereiche

## 7.1 XJustiz-Nachricht „uebermittlungSchriftgutobjekte"

Die Nachricht `nachricht.gds.uebermittlungSchriftgutobjekte.0005005` ist allgemeingültig und auch für den Dokumentenaustausch zwischen anderen Beteiligten geeignet (z.B. zwischen Behörden und Rechtsanwälten).

Sie enthält immer:

### Nachrichtenkopf (Pflicht)

> Wer schickt die EGVP-Nachricht aus welchem Anlass an wen?

- Absender und Empfänger (Pflicht)
- Nachrichten-ID (Pflicht)
- Erstellungszeitpunkt (Pflicht)
- Aktenzeichen von Absender und Empfänger
- Kommunikationsanlass
- Sendungspriorität

> **Hinweis:** Das Element „nachrichtenuebergreifenderProzess" ist **nur** für den justizinternen Datenaustausch. Verfahrensbeteiligte dürfen es **nicht** nutzen.

### Grunddaten (optional)

> Welches Verfahren führen Absender und Empfänger? Welche Personen sind beteiligt?

- Verfahrensdaten (Verfahrensgegenstand, Sachgebiet, Kurzrubrum)
- Beteiligte Personen (Kläger, Beklagter, Zeuge, Gutachter…)

### Schriftgutobjektdaten (Pflicht)

> Welche Akten/Dokumente sind Bestandteil der Übermittlung?

- Angaben zu Schriftsätzen oder zur Akte
- Datum, Reihenfolge, Dokumentenart, Dateinamen

### 7.1.1 Verknüpfung von Daten innerhalb einer XJustiz-Nachricht

Verfahrensdaten und Beteiligtendaten werden in den Grunddaten angegeben. Akten können über eine **Beteiligtennummer** mit Beteiligten verknüpft werden:

1. Beteiligtennummer in den Grunddaten vergeben
2. Beteiligtennummer im Element „Person" bei den Aktenangaben referenzieren

### 7.1.2 Zuordnung zum richtigen Vorgang

Die Zuordnung erfolgt über die jeweiligen **Aktenzeichen** im Nachrichtenkopf.

## 7.2 XJustiz-Nachricht „rücklaufendes eEB"

Für die Rücksendung des elektronischen Empfangsbekenntnisses (eEB) wird im Nachrichtenkopf Bezug auf die empfangene Nachricht genommen:

- **eigeneNachrichtenID** → wird beim Empfänger als **fremdeNachrichtenID** zurück übermittelt
- Absender des eEB wird im Nachrichtenkopf angegeben
- Empfangsdatum wird eingetragen

### 7.2.1 Zustellungsempfänger gibt das eEB selbst ab

Der angegebene Empfänger der eEB-Anforderung erstellt das rücklaufende eEB selbst. Er wird als Absender aufgeführt.

### 7.2.2 Abweichender Zustellungsempfänger (z.B. Behörde)

Wenn der Zustellungsempfänger von der Person abweicht, die das eEB abgibt (z.B. Behörde statt natürliche Person), muss der **abweichende Zustellungsempfänger als Absender** angegeben werden.

### 7.2.3 Abweichender Zustellungsempfänger als Vertreter

Ein Vertreter kann das eEB abgeben. Der abweichende Zustellungsempfänger wird als Absender angegeben und **„Zustellungsempfänger abweichend" = Ja** gesetzt.

### 7.2.4 Das eEB wird nicht abgegeben

Mögliche Gründe:
- Zustellungsempfänger **nicht am Verfahren beteiligt**
- Inhalt der Sendung **unklar oder unvollständig**
- **Signaturprüfung** der übermittelten Dokumente fehlgeschlagen

Eine nähere Erläuterung kann angegeben werden.

## 7.3 Austausch von Schriftgutobjekten

Die Anhänge werden von den EGVP-Komponenten im Regelfall **alphabetisch sortiert** – eine fachliche Reihenfolge kann nicht gebildet werden. Die Informationen für die Aufbereitung stehen in den **Schriftgutobjektdaten** der XJustiz-Nachricht.

### Struktur der Schriftgutobjekte

```
Schriftgutobjekte
├── Anschreiben (Referenz auf ein Dokument)
├── Akte
│   ├── Teilakte 1
│   │   ├── Dokument 1 → Datei(en)
│   │   └── Dokument 2 → Datei(en)
│   └── Teilakte 2
│       └── Dokument 1 → Datei(en)
└── Dokumente (einzelne Schriftsätze)
    ├── Dokument 1 → Datei(en)
    └── Dokument 2 → Datei(en)
```

> **Hinweis:** Das Element „justizinterneDaten" darf von Verfahrensbeteiligten **nicht** genutzt werden.

### 7.3.1 Kennzeichnung des Anschreibens

Das Anschreiben muss im Container **„Akte" oder „Dokumente"** aufgeführt werden und zusätzlich im Container **„Anschreiben"** per UUID referenziert werden (Element `ref.sgo`).

Vorbereitende Schriftsätze, Anträge und Erklärungen nach § 130a Abs. 1 ZPO sollen **nicht** als Anschreiben gekennzeichnet werden.

### 7.3.2 Reihenfolge der Dokumente

Element **„nummerImUebergeordnetenContainer"** gibt die Reihenfolge an:
- Beginnt in jedem Container mit **1**
- Fortlaufend, **ohne Auslassungen**
- Gilt jeweils für den übergeordneten Container

### 7.3.3 Zitierung von Akteninhalten

Zitierung über:
- **Paginierungsinformation** auf den Repräsentaten (bevorzugt)
- Alternativ: Datum, Verfasser und Seitenzahl der Einzeldokumente

### 7.3.4 Kennzeichnung von Scanprodukten

| Element | Beschreibung |
|---------|-------------|
| `scanDatum` | Datum des Scans (kennzeichnet auch als Scanprodukt) |
| `ersetzenderScan` | Kennzeichnet ersetzendes Scannen |

### 7.3.5 Mehrere Dateien = ein Dokument

Für jedes Dokument können beliebig viele Dateien angegeben werden. Der **Bestandteiltyp** gibt an, um welchen Typ es sich handelt:

| Bestandteiltyp | Beschreibung |
|---------------|-------------|
| Original | Ursprüngliche Datei (max. 1 pro Dokument) |
| Repräsentat | PDF/A-Version (max. 1 pro Dokument) |
| Signaturdatei | Zugehörige Signatur (über `dateiname.bezugsdatei` verknüpft) |
| Signaturprüfprotokoll | Ergebnis der Signaturprüfung |
| Prüfvermerk | Prüfvermerk |
| Transfervermerk | Transfervermerk |
| VHN | Vertrauenswürdiger Herkunftsnachweis |
| Hinlaufendes eEB | eEB-Anforderung |

> Bei Aktenübersendung im Regelfall: Werte **„Repräsentat"** und **„Signaturprüfprotokoll" / „Prüfvermerk"** verwenden.

### 7.3.6 Fachlicher Zusammenhang zwischen Dokumenten

Über das Element **„Verweis"** kann eine fachliche Verknüpfung hergestellt werden:
- Immer vom **untergeordneten** auf das **übergeordnete** Schriftgutobjekt verweisen
- Beispiel: Anlage → Schriftsatz, Berichtigungsbeschluss → Urteil
- Typen: untrennbare Verbindung, Anlage, einfache Verbindung

### 7.3.7 Erkennung bereits übermittelter Dokumente

Bei erneuter Übermittlung (z.B. fortgeschriebene Akte) soll das Dokument die **gleiche UUID** erhalten. Der Empfänger kann durch UUID-Vergleich erkennen, ob es bereits übermittelt wurde.

Bei **inhaltlicher Änderung** → neue UUID (= neues Dokument).
