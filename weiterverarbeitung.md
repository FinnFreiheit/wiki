---
layout: page
title: 6 – Weiterverarbeitung
nav_order: 6
---

# Weiterverarbeitung der von der Justiz übermittelten Nachrichten

## 6.1 Übernahme in E-Aktensysteme oder Fachverfahren

Soweit keine fachlichen Gründe entgegenstehen, muss der Empfänger die EGVP-Nachricht **nicht als Ganzes** in der E-Akte speichern. Es sind lediglich die übermittelten **Dokumente** zu übernehmen.

Zusätzlich sollten folgende Prüfdokumente zur Akte genommen werden:
- **Prüfvermerk**
- **Eingangsbestätigung**
- ggf. **Prüfprotokoll**

### Fachliche Fragestellungen aus dem Prüfvermerk

| Frage | Information |
|-------|-------------|
| Wer hat was eingereicht? | Absender, Dokumentenliste, Formate, Übermittlungsweg |
| Wann ist die Nachricht eingegangen? | Eingangszeitpunkt |
| Für welche Dokumente ist die Schriftform erfüllt? | Sicherer Übermittlungsweg oder qeS |

### VHN-Datei

Zusätzlich kann die Datei `vhn.xml` (vertrauenswürdiger Herkunftsnachweis) nebst Signaturdatei gespeichert und mit den referenzierten Dokumenten verknüpft werden. Sie dient auch der Unterstützung im Supportfall (enthält Herstellerangaben zur Software).

## 6.2 Übernahme in die Papierakte

Sofern Dokumente ausgedruckt und zur Papierakte genommen werden, sind die Umstände des elektronischen Eingangs zu dokumentieren. Hierzu genügt es, den **Prüfvermerk auszudrucken und abzuheften**.

## 6.3 Übermittlung der Dokumente an Dritte

Sofern ein Dokument an einen anderen Beteiligten weitergeleitet werden soll, kann der **Prüfvermerk als Integritäts- und Authentizitätsnachweis** beigefügt werden.

## 6.4 Verteilung innerhalb des eigenen Verantwortungsbereichs

Für das Routing können folgende Elemente der `xjustiz_nachricht.xml` genutzt werden:

- **Name der XJustiz-Nachricht**
- Element **„Aktenzeichen Empfänger"** im Nachrichtenkopf
- Element **„Sachgebiet"** in den Grunddaten/Instanzdaten
- Element **„Ereignis"** im Nachrichtenkopf

## 6.5 Weiterleitung von Nachrichten

Der Standard für die Weiterleitung von Nachrichten ermöglicht die maschinelle Weiterverarbeitung. Der Empfänger soll erkennen können:

- Dass es sich um eine **weitergeleitete Nachricht** handelt
- Von welchem **Absender** sie stammt
- An welchen **Empfänger** sie gerichtet ist
- **Wann** die Nachricht beim ursprünglichen Empfänger eingegangen ist

> **Gültigkeit:** Der Standard gilt seit 01.12.2023 und muss seit 01.12.2024 umgesetzt sein.

### 6.5.1 Anlagen der Weiterleitungsnachricht

Für die Weiterleitung ist eine **neue EGVP-Nachricht** zu erstellen. Diese enthält:

- ✅ Alle **Anhänge der ursprünglichen Nachricht** als Einzeldateien
- ✅ Die **xjustiz_nachricht.xml** der ursprünglichen Nachricht
- ✅ Den **Prüfvermerk** (PDF + XML)
- ✅ Den **VHN** (vhn.xml + vhn.xml.p7s)
- ❌ **Keine** weiteren Prüfdateien (z.B. Prüfprotokolle)
- ❌ **Keine** zusätzlichen Anhänge
- ❌ **Nicht** im ZIP-Format

### 6.5.2 Dateinamen bei Weiterleitung

Die Dateien der ursprünglichen Nachricht müssen um eine **eigene UUID** ergänzt werden:

| Ursprünglicher Dateiname | Neuer Dateiname |
|--------------------------|-----------------|
| `xjustiz_nachricht.xml` | `xjustiz_nachricht_UUIDa.xml` |
| `pruefvermerk.pdf` | `pruefvermerk_UUIDb.pdf` |
| `pruefvermerk.xml` | `pruefvermerk_UUIDc.xml` |
| `vhn.xml` | `vhn_UUIDd.xml` |
| `vhn.xml.p7s` | `vhn_UUIDd.xml.p7s` |

> Die Dateinamen der **Dokumentanlagen** der ursprünglichen Nachricht dürfen **nicht** geändert werden.

### 6.5.3 XJustiz-Nachricht für die Weiterleitungsnachricht

Für die Weiterleitungsnachricht ist eine **neue** `xjustiz_nachricht.xml` zu erstellen.

**Nachrichtenkopf:**
- Element Ereignis: Wert **289 „Weiterleitung einer Nachricht"**
- Absender: derjenige, der weiterleitet
- Empfänger: der Adressat der Weiterleitung
- Sendungspriorität und Vertraulichkeit aus der ursprünglichen Nachricht übernehmen

**Schriftgutobjekte:**
- Nur **ein** `Type.GDS.Dokument`
- Dokumentenklasse: **014 Technische Information**

| Dateiname | Bestandteiltyp (XJustiz 3.5) |
|-----------|------------------------------|
| `xjustiz_nachricht_UUIDa.xml` | 001, Original |
| `pruefvermerk_UUIDb.pdf` | 010, Prüfvermerk |
| `pruefvermerk_UUIDc.xml` | 010, Prüfvermerk |
| `vhn_UUIDd.xml` | 011, VHN |
| `vhn_UUIDd.xml.p7s` | 003, Signaturdatei |
