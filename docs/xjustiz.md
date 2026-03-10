# 7. XJustiz

Dank der maschinenlesbaren strukturierten Daten im XJustiz-Format können Nachrichteninhalte automatisiert an die richtigen IT-Systeme ausgesteuert oder an den richtigen Bearbeiter weitergeleitet werden. Darüber hinaus ermöglicht XJustiz die automatisierte Übernahme von Daten in die IT-Systeme der Empfänger.

Der Standard wird von der **Bund-Länder-Kommission für Informationstechnik in der Justiz (BLK)** herausgegeben und ist frei verfügbar auf [www.xjustiz.de](https://www.xjustiz.de).

!!! info "Jährliches Release"
    Einmal jährlich wird eine neue XJustiz-Version gültig. Sie löst die bis dahin gültige Version ab und wird 12 Monate vor Gültigkeit veröffentlicht.

## XJustiz-Nachrichten

Für die verschiedenen fachlichen Kommunikationsanlässe sind XJustiz-Nachrichten vorgesehen:

- **Basisnachricht** – fachübergreifend
- **Übermittlung Schriftgutobjekte** – fachübergreifend (`nachricht.gds.uebermittlungSchriftgutobjekte.0005005`)
- **Fachnachrichten** – für spezielle Kommunikationsanlässe

Die XJustiz-Nachricht trägt immer den Dateinamen **`xjustiz_nachricht.xml`**.

## 7.1 XJustiz-Nachricht „uebermittlungSchriftgutobjekte"

Diese Nachricht enthält immer einen **Nachrichtenkopf** und **Schriftgutobjekte**. Optional auch **Grunddaten**.

### Aufbau

| Bereich | Inhalt | Beschreibung |
|---------|--------|-------------|
| **Nachrichtenkopf** | Wer → an wen, warum? | Absender, Empfänger, Aktenzeichen, Anlass, Sendungspriorität |
| **Grunddaten** | Welches Verfahren? Wer ist beteiligt? | Verfahrensgegenstand, Sachgebiet, Kurzrubrum, beteiligte Personen |
| **Fachdaten** | Fachspezifische Informationen | z. B. Angaben zum Bußgeldbescheid |
| **SGO-Daten** | Welche Akten/Dokumente? | Datum, Reihenfolge, Dokumentenart, Dateinamen |

!!! warning "Nicht verwenden"
    Das Element **„nachrichtenuebergreifenderProzess"** findet nur für den justizinternen Datenaustausch Verwendung. Für Nachrichten von Verfahrensbeteiligten an Gerichte/Staatsanwaltschaften darf es nicht genutzt werden.

### 7.1.1 Verknüpfung von Daten

In den Grunddaten werden Verfahrensdaten sowie Daten zu den Beteiligten angegeben. In den Schriftgutobjekten können Akten mit Beteiligten verknüpft werden über:

- **Beteiligtennummer** in den Grunddaten
- Element **„Person"** mit `Type.GDS.Ref.Beteiligtennummer` bei den Akten

### 7.1.2 Zuordnung beim Empfänger

Für die Zuordnung zum Verfahren werden die jeweiligen **Aktenzeichen im Nachrichtenkopf** übermittelt.

## 7.2 XJustiz-Nachricht „rücklaufendes eEB"

Für die Rücksendung des elektronischen Empfangsbekenntnisses wird die ID der empfangenen Nachricht (`eigeneNachrichtenID`) im Element **`fremdeNachrichtenID`** zurück übermittelt.

### 7.2.1 Zustellungsempfänger gibt das eEB ab

Der Empfänger, der in der XJustiz-Nachricht des hinlaufenden eEBs angegeben ist, wird im rücklaufenden eEB als **Absender** aufgeführt.

### 7.2.2 Abweichender Zustellungsempfänger (bei Behörde o. ä.)

Wenn der adressierte Zustellungsempfänger von der Person, die das eEB abgibt, abweicht, muss der **abweichende Zustellungsempfänger als Absender** angegeben werden (z. B. wenn eine Behörde statt einer natürlichen Person adressiert ist).

### 7.2.3 Abweichender Zustellungsempfänger als Vertreter

Ein Vertreter kann das eEB abgeben. Zusätzlich muss **„Ja"** im Element **„Zustellungsempfänger abweichend"** angegeben werden.

### 7.2.4 eEB wird nicht abgegeben

Wenn das eEB nicht abgegeben werden soll, muss ein Grund angegeben werden:

- Zustellungsempfänger nicht am Verfahren beteiligt
- Inhalt der Sendung unklar oder unvollständig
- Signaturprüfung der übermittelten Dokumente fehlgeschlagen

Eine nähere Erläuterung kann optional angegeben werden.

## 7.3 Austausch von Schriftgutobjekten

Die Anhänge werden von den EGVP-Komponenten im Regelfall **alphabetisch sortiert**. Die fachliche Reihenfolge muss daher über die **Schriftgutobjektdaten** in der XJustiz-Nachricht hergestellt werden.

!!! warning "Nicht verwenden"
    Das Element **„justizinterneDaten"** darf von Verfahrensbeteiligten nicht genutzt werden.

### Struktur

```
Schriftgutobjekte
├── Anschreiben
├── Akte
│   ├── Teilakte 1
│   │   ├── Dokument 1 → Datei(en)
│   │   └── Dokument 2 → Datei(en)
│   └── Teilakte 2
│       └── Dokument 1 → Datei(en)
└── Dokument (einzeln)
    └── Datei(en)
```

### 7.3.1 Kennzeichnung des Anschreibens

Das Anschreiben muss entweder im Container „Akte" oder „Dokumente" aufgeführt werden. Zur maschinellen Erkennung wird die UUID im Container **„Anschreiben"** (Element `ref.sgo`) referenziert.

!!! info "Hinweis"
    Vorbereitende Schriftsätze und deren Anlagen (§ 130a Abs. 1 ZPO) werden üblicherweise **nicht** als Anschreiben gekennzeichnet, da es sich nicht um Erläuterungen der Sendung handelt.

### 7.3.2 Reihenfolge der Dokumente

Element **`nummerImUebergeordnetenContainer`** gibt die Reihenfolge an. Die Nummer beginnt in jedem Container mit **1**. Auslassungen sind nicht zulässig.

### 7.3.3 Zitierung von Akteninhalten

Sofern Paginierungsinformation auf den Repräsentaten aufgebracht ist, kann diese für die Zitierung genutzt werden. Andernfalls: Datum, Verfasser und Seitenzahl der Einzeldokumente.

### 7.3.4 Kennzeichnung von Scanprodukten

Im Container „Dokument" stehen zur Verfügung:

- Element **`scanDatum`** – Datum des Scans (kennzeichnet gleichzeitig als Scanprodukt)
- Element **`ersetzenderScan`** – kennzeichnet ersetzendes Scannen

### 7.3.5 Mehrere Dateien pro Dokument

Für jede Datei muss der **Bestandteiltyp** angegeben werden:

| Typ | Beschreibung |
|-----|-------------|
| Original | Das Ausgangsdokument |
| Repräsentat | PDF/A-Version (max. einmal) |
| Signaturdatei | Über `dateiname.bezugsdatei` mit signierter Datei verbinden |
| Signaturprüfprotokoll | Ergebnis der Signaturprüfung |
| Prüfvermerk | Nachweis der Übermittlung |
| Transfervermerk | Übertragungsnachweis |
| VHN | Vertrauenswürdiger Herkunftsnachweis |
| Hinlaufendes eEB | Empfangsbekenntnisanforderung |

Pro Dokument darf nur **ein Original** und **ein Repräsentat** übermittelt werden.

### 7.3.6 Fachlicher Zusammenhang zwischen Dokumenten

Über das Element **„Verweis"** kann eine fachliche Verknüpfung hergestellt werden. Verweise gehen stets vom untergeordneten zum übergeordneten Schriftgutobjekt (z. B. Anlage → Schriftsatz).

Verknüpfungsarten:

- Untrennbare Verbindung
- Anlage
- Einfache Verbindung

### 7.3.7 Erkennung bereits übermittelter Dokumente

Wenn ein Dokument erneut übermittelt wird (z. B. fortgeschriebene Akte), soll es im Element **`Identifikation/ID`** die **gleiche UUID** wie bei der ersten Übermittlung erhalten. Inhaltlich geänderte Dokumente erhalten eine neue ID.
