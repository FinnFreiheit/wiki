---
layout: page
title: 5 – Inhalt der Nachrichten
nav_order: 5
---

# Inhalt der Nachrichten

Eine EGVP-Nachricht darf immer nur **genau ein Verfahren** des adressierten Gerichts oder der adressierten Staatsanwaltschaft betreffen.

## Grundstruktur einer EGVP-Nachricht

Eine EGVP-Nachricht enthält grundsätzlich als Anlagen (Attachments):

1. Eine bestimmte Anzahl von **Dokumenten** (siehe [Kapitel 4 – Größe]({{ '/uebermittlung/' | relative_url }}))
2. Eine **XJustiz-Nachricht** im XML-Format (`xjustiz_nachricht.xml`), die den Inhalt in strukturierter, maschinenlesbarer Form beschreibt

Die XJustiz-Nachricht enthält u.a.:
- Ob es sich um einzureichende Schriftsätze oder eine Akte handelt
- Art des Dokumentes (Klage, Urteil, Beschluss…)
- Informationen zur inhaltlichen Erschließung

## 5.1 Strukturierter maschinenlesbarer Datensatz

Jeder EGVP-Nachricht **muss** ein strukturierter Datensatz gemäß dem XJustiz-Standard als Anlage im XML-Format beigefügt werden. Die XJustiz-Nachricht muss immer den Dateinamen **`xjustiz_nachricht.xml`** tragen.

### Pflichtangaben der XJustiz-Nachricht

Jede XJustiz-Nachricht enthält mindestens:

- **Absender** der Nachricht
- **Empfänger** der Nachricht
- **Sachgebiet**
- **Aktenzeichen des Empfängers**
  - Bei verfahrenseinleitenden Dokumenten: `neu`
  - Bei unbekanntem Aktenzeichen: `unbekannt`

Darüber hinaus sollen möglichst viele weitere Daten enthalten sein, mindestens die in § 2 Abs. 3 ERVV aufgeführten Daten.

> **Wichtig:** In der XJustiz-Nachricht müssen alle Dateien, die mit der Nachricht versendet werden, aufgeführt werden.

### Führende vs. Hilfsdaten

Die Daten einer XJustiz-Nachricht sind grundsätzlich **Hilfsdaten** für die maschinelle Verarbeitung. In bestimmten gesetzlich geregelten Szenarien (z.B. beim eEB, § 173 ZPO) stellen die XJustiz-Daten die **führenden Daten** dar. Für führende Daten wird empfohlen, sie aufzubewahren.

## 5.2 Vorgaben für die Dateinamen

### Allgemeine Regeln

| Regel | Beschreibung |
|-------|-------------|
| Eindeutigkeit | Keine identischen Dateinamen in einer EGVP-Nachricht |
| Syntax | `Dokumentname_UUID.Dateiformat` (empfohlen) |
| Maximale Länge | **90 Zeichen** inkl. Dateiendung |
| Erlaubte Zeichen | Buchstaben (inkl. Ä, ä, Ö, ö, Ü, ü, ß), Ziffern, Unterstrich, Minus |
| Punkte | Nur als Trennzeichen zwischen Name und Endung (Ausnahme: abgesetzte Signaturdateien) |

### Signaturdateien

- Signaturdateien erhalten **exakt denselben Dateinamen** wie die signierte Datei (mit abweichendem Dateiformat)
- Beispiel: `Klage_UUID.pdf` → `Klage_UUID.pdf.pkcs7`
- Jede weitere Signaturdatei muss einen abweichenden Dateinamen erhalten

### XJustiz-Dateinamen

- Haupt-XJustiz-Nachricht: immer **`xjustiz_nachricht.xml`**
- Zusätzliche XJustiz-Nachrichten (z.B. bei Weiterleitung): **`xjustiz_nachricht_UUID.xml`**

### Nummerierung

Wenn Dateien ausnahmsweise nicht in der XJustiz-Nachricht aufgeführt werden können, sollen die Dateinamen eine **logische Nummerierung** enthalten.

## 5.3 Anforderungen an die Dokumente

### Dateiformate

- Elektronische Dokumente müssen im **PDF-Format** als Einzeldateien eingereicht werden
- Bei Darstellungsproblemen zusätzlich im **TIFF-Format**
- Für **elektronische Beweismittel** gelten keine Formatbeschränkungen
- **ZIP-Dateien** sind **nicht** zulässig

### Scan-Anforderungen

Bei eingescannten Papierdokumenten:
- Auflösung wählen, die zu möglichst **geringer Dateigröße** führt, aber Inhalte vollständig darstellt
- Zu große Dateien können abgewiesen werden

### Verschlüsselung

Auf **zusätzliche Verschlüsselung** sowie **Einschränkungen der Leserechte** ist zu verzichten – die Sicherheit wird bereits durch die doppelte Verschlüsselung in der EGVP-Infrastruktur sichergestellt.

## 5.4 Anforderungen bei der Übersendung von Akten

Behördenakten sollen gemäß § 2 Abs. 2 BehAkÜbV über einen sicheren Übermittlungsweg eingereicht werden.

### 5.4.1 Struktur der Akte

- Dokumente als **Einzeldokumente** im PDF-Format einreichen
- **Nicht** in einem Gesamt-PDF zusammenfassen
- Vor dem Versand in PDF umwandeln, wenn Dokumente in anderem Format geführt werden
- Ausgangsdokumente müssen nicht übermittelt werden (es wird von PDF-Repräsentaten ausgegangen)

**Ausnahmen** für das ursprüngliche Format (z.B. Excel):
1. Wenn inhaltstragende Informationen bei PDF-Konvertierung verloren gehen
2. Wenn es zur besseren Bearbeitbarkeit oder Lesbarkeit erforderlich ist

### Signaturdateien bei Aktenübermittlung

- Signaturdateien **sollen nicht** übermittelt werden (§ 2 Abs. 3 S. 1 BehAkÜbV)
- Signaturprüfprotokolle **können** übermittelt werden
- Auf Nachforderung der Gerichte: Ursprungsdokumente inkl. Signaturdateien zu übermitteln
- Irreversible Markierungen, Stempel, Kommentare müssen mit übermittelt werden

### XJustiz-Nachricht für Akten

Zusätzlich zu den Dokumenten soll eine XJustiz-Nachricht übermittelt werden mit mindestens:

1. Daten gemäß § 2 Abs. 3 ERVV
2. **Aktenzeichen** der übermittelnden Stelle
3. **Reihenfolge** der Dokumente in der Akte
4. **Typ** der Dokumente der Akte
5. **Eingangsdatum** der Dokumente der Akte

### 5.4.2 Paginierungsinformationen

- Durchlaufende Paginierung auf den Seiten der Einzel-PDF-Dokumente
- Fortlaufende Nummerierung auch bei erneuter Übersendung oder Nachreichung
- Für entfernte Dokumente: **Fehlblätter** mit Grund des Fehlens anlegen
