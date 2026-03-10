# 6. Weiterverarbeitung der von der Justiz übermittelten Nachrichten

## 6.1 Übernahme in E-Aktensysteme oder Fachverfahren

Soweit keine fachlichen Gründe entgegenstehen, muss der Empfänger die EGVP-Nachricht **nicht als Ganzes** in der E-Akte speichern. Es sind lediglich die **übermittelten Dokumente** zu übernehmen.

Zusätzlich sollten folgende Prüfdokumente zur E-Akte genommen werden:

- Prüfvermerk
- Eingangsbestätigung
- ggf. Prüfprotokoll

### Fachliche Nachweisfunktion des Prüfvermerks

Der Prüfvermerk beantwortet folgende Fragen:

- **Wer** hat **welche Dokumente** in **welchem Format** auf **welchem Übermittlungsweg** eingereicht?
- **Wann** ist die Nachricht eingegangen?
- Für welche Dokumente ist die **Schriftform** erfüllt?

Zusätzlich kann die Datei `vhn.xml` (vertrauenswürdiger Herkunftsnachweis) nebst Signaturdatei gespeichert und mit den referenzierten Dokumenten verknüpft werden.

## 6.2 Übernahme in die Papierakte

Sofern Dokumente ausgedruckt und zur Papierakte genommen werden, sind die Umstände des elektronischen Eingangs zu dokumentieren. Hierzu genügt es, den **Prüfvermerk** auszudrucken und abzuheften.

## 6.3 Übermittlung der Dokumente an Dritte

Wenn ein Dokument, das auf einem sicheren Übermittlungsweg übermittelt wurde, an einen anderen Beteiligten weitergeleitet werden soll, kann der **Prüfvermerk als Integritäts- und Authentizitätsnachweis** beigefügt werden.

## 6.4 Verteilung innerhalb des eigenen Verantwortungsbereichs

Für das automatisierte technische Routing können folgende Elemente aus der `xjustiz_nachricht.xml` genutzt werden:

- Name der XJustiz-Nachricht
- Element **„Aktenzeichen Empfänger"** im Nachrichtenkopf
- Element **„Sachgebiet"** in den Grunddaten/Instanzdaten
- Element **„Ereignis"** im Nachrichtenkopf

## 6.5 Weiterleitung von Nachrichten

!!! info "Standard gültig seit 01.12.2023"
    Umsetzungspflicht spätestens bis zum 01.12.2024.

Die Komfortfunktion „Weiterleitung von Nachrichten" ermöglicht die Weiterleitung ohne darüber hinausgehenden Erklärungsgehalt. Der Empfänger soll erkennen können:

- **dass** es sich um eine weitergeleitete Nachricht handelt
- **von wem** (bestimmter Absender)
- **an wen** (bestimmter Empfänger)
- **wann** diese Nachricht beim ursprünglichen Empfänger eingegangen ist

Für die Weiterleitung ist **zwingend eine neue EGVP-Nachricht** zu erstellen.

### 6.5.1 Anlagen der Weiterleitungsnachricht

Die neue Nachricht enthält im Attachments-Ordner:

- ✅ Alle Anhänge der ursprünglichen Nachricht als Einzeldateien
- ✅ Die `xjustiz_nachricht.xml` der ursprünglichen Nachricht
- ✅ Prüfvermerk im PDF- und XML-Format (`pruefvermerk.pdf`, `pruefvermerk.xml`)
- ✅ VHN (`vhn.xml`, `vhn.xml.p7s`) der ursprünglichen Nachricht

!!! danger "Nicht zulässig"
    - Prüfprotokolle der ursprünglichen Nachricht dürfen **nicht** übernommen werden
    - Weitere Anhänge dürfen **nicht** ergänzt werden
    - ZIP-Format ist **nicht** zulässig

### 6.5.2 Dateinamen

Die Dateien der ursprünglichen Nachricht müssen um eine eigene UUID ergänzt werden:

| Ursprüngliche Datei | Weiterleitungsnachricht |
|---------------------|------------------------|
| `xjustiz_nachricht.xml` | `xjustiz_nachricht_UUIDa.xml` |
| `pruefvermerk.pdf` | `pruefvermerk_UUIDb.pdf` |
| `pruefvermerk.xml` | `pruefvermerk_UUIDc.xml` |
| `vhn.xml` | `vhn_UUIDd.xml` |
| `vhn.xml.p7s` | `vhn_UUIDd.xml.p7s` |

Die Dateinamen der **Anlagen** der ursprünglichen Nachricht dürfen **nicht** geändert werden.

### 6.5.3 XJustiz-Nachricht für die Weiterleitungsnachricht

Für die Weiterleitungsnachricht ist eine **neue `xjustiz_nachricht.xml`** zu erstellen mit der Nachricht `nachricht.gds.uebermittlungSchriftgutobjekte.0005005`.

**Nachrichtenkopf:**

- Element Ereignis: **Wert 289 „Weiterleitung einer Nachricht"**
- Absender: derjenige, der die Nachricht weiterleitet
- Empfänger: Adressat der Weiterleitung
- Sendungspriorität und Vertraulichkeit aus der ursprünglichen Nachricht übernehmen

**Schriftgutobjekte:**

Nur ein `Type.GDS.Dokument` mit folgenden Dateien:

| Dateiname | Bestandteiltyp (XJustiz 3.4) | Bestandteiltyp (XJustiz 3.5) |
|-----------|------------------------------|------------------------------|
| `xjustiz_nachricht_UUIDa.xml` | 001, Original | 001, Original |
| `pruefvermerk_UUIDb.pdf` | 010, Prüfvermerk | 010, Prüfvermerk |
| `pruefvermerk_UUIDc.xml` | 010, Prüfvermerk | 010, Prüfvermerk |
| `vhn_UUIDd.xml` | 009, Fachliches Metadatum | 011, VHN |
| `vhn_UUIDd.xml.p7s` | 003, Signaturdatei | 003, Signaturdatei |
