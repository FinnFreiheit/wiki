# 5. Inhalt der Nachrichten

Eine EGVP-Nachricht darf aus technisch-organisatorischen Gründen immer nur **genau ein Verfahren** des adressierten Gerichts oder der adressierten Staatsanwaltschaft betreffen.

Eine EGVP-Nachricht enthält grundsätzlich als Anlagen (Attachments):

- eine bestimmte Anzahl von **Dokumenten**
- eine **XJustiz-Nachricht** im XML-Format (`xjustiz_nachricht.xml`), die den Inhalt der Sendung in strukturierter, maschinenlesbarer Form beschreibt

## 5.1 Strukturierter maschinenlesbarer Datensatz

Jeder EGVP-Nachricht **muss** ein strukturierter maschinenlesbarer Datensatz gemäß dem XJustiz-Standard als Anlage im XML-Format beigefügt werden. Die XJustiz-Nachricht muss immer den Dateinamen **`xjustiz_nachricht.xml`** tragen.

### Pflichtangaben

Jede XJustiz-Nachricht enthält mindestens:

- **Absender** der Nachricht
- **Empfänger** der Nachricht
- **Sachgebiet**
- **Aktenzeichen des Empfängers** (Bei verfahrenseinleitenden Dokumenten: „neu". Wenn unbekannt: „unbekannt".)

Darüber hinaus sollen möglichst viele weitere Daten enthalten sein, mindestens die Daten gemäß § 2 Abs. 3 ERVV.

!!! info "Alle Dateien auflisten"
    In der XJustiz-Nachricht **müssen** alle Dateien aufgeführt werden, die mit der Nachricht versendet werden.

### Führende vs. Hilfsdaten

Die Daten einer XJustiz-Nachricht sind grundsätzlich **Hilfsdaten** der maschinellen Datenverarbeitung. In bestimmten, gesetzlich geregelten Szenarien (z. B. eEB, § 173 ZPO) stellen die XJustiz-Daten die **führenden Daten** dar. Für führende XJustiz-Daten wird empfohlen, sie aufzubewahren.

## 5.2 Vorgaben für die Dateinamen

### Regeln

| Regel | Beschreibung |
|-------|-------------|
| Eindeutigkeit | Keine Dateien mit identischen Dateinamen in einer EGVP-Nachricht |
| Namensbildung | Syntax: `Dokumentname_UUID.Dateiformat` |
| Länge | Maximal **90 Zeichen** inkl. Dateiendungen |
| Erlaubte Zeichen | Buchstaben (inkl. Ä, ä, Ö, ö, Ü, ü, ß), Ziffern, Unterstrich, Minus |
| Punkte | Nur als Trennzeichen vor der Dateiendung (Ausnahme: abgesetzte Signaturdateien) |
| XJustiz-Dateiname | Immer `xjustiz_nachricht.xml` |

### Signaturdateien

Signaturdateien erhalten **exakt denselben Dateinamen** wie die signierte Datei, mit der Endung der Signaturdatei:

- Beispiel: `Klage_UUID.pdf` → `Klage_UUID.pdf.pkcs7`

Jede weitere Signaturdatei muss einen abweichenden Dateinamen erhalten (z. B. durch Ergänzung einer Ziffer).

### Weitere XJustiz-Nachrichten

Wenn weitere XJustiz-Nachrichten (z. B. bei Weiterleitung) beigefügt werden, muss dem Dateinamen eine UUID angestellt werden: `xjustiz_nachricht_UUID.xml`.

## 5.3 Anforderungen an die Dokumente

- Elektronische Dokumente **müssen im PDF-Format** als Einzeldateien eingereicht werden
- Zusätzlich im TIFF-Format möglich, wenn bildliche Darstellungen nicht verlustfrei in PDF wiedergegeben werden
- Für **elektronische Beweismittel** gelten keine Formatbeschränkungen

!!! danger "Nicht zulässig"
    Der Versand in Form einer **ZIP-Datei** ist nicht zulässig.

### Scan-Anforderungen

Eingescannte Papierdokumente sollen mit einer Auflösung gescannt werden, die:

- zu einer möglichst **geringen Dateigröße** führt
- die Inhalte noch **vollständig darstellt**

### Verschlüsselung

Da die Sicherheit durch die doppelte Verschlüsselung in der EGVP-Infrastruktur sichergestellt ist, ist auf eine **zusätzliche Verschlüsselung** sowie auf Einschränkungen der Leserechte zu verzichten.

## 5.4 Anforderungen bei der Übersendung von Akten

Behördenakten sollen gemäß § 2 Abs. 2 BehAkÜbV über einen sicheren Übermittlungsweg eingereicht werden.

### 5.4.1 Struktur der Akte

- Dokumente sollen als **Einzeldokumente** im **PDF-Format** eingereicht werden
- Dokumente dürfen **nicht in einem Gesamt-PDF** zusammengefasst werden
- Nicht-PDF-Dokumente sollen vor dem Versand in PDF umgewandelt werden

Die XJustiz-Nachricht (§ 2 Abs. 4 BehAkÜbV) muss mindestens enthalten:

1. Die in § 2 Abs. 3 ERVV genannten Daten
2. Das Aktenzeichen der übermittelnden Stelle
3. Angaben zur **Reihenfolge** der Dokumente
4. Angaben zum **Typ** der Dokumente
5. Das **Eingangsdatum** der Dokumente

### 5.4.2 Paginierungsinformationen

Die Paginierung soll durchlaufend auf den Seiten der Einzel-PDF-Dokumente angegeben werden. Dabei ist sicherzustellen, dass die Nummerierung auch bei erneuter Übersendung oder Nachreichung nicht abweicht.

Für entfernte Dokumente sollen **Fehlblätter** mit Information zum Grund des Fehlens zur Akte genommen werden.
