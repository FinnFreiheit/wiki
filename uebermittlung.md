---
layout: page
title: 4 – Übermittlung der Nachrichten
nav_order: 4
---

# Übermittlung der Nachrichten

Der Austausch von Dokumenten, Akten und strukturierten Datensätzen auf einem sicheren Übermittlungsweg erfolgt über die **Infrastruktur des EGVP** unter Verwendung des beA, beN, beSt, beBPo, eBO oder des MJP.

## 4.1 Beteiligte Kommunikationspartner

Eine EGVP-Nachricht wird immer zwischen **genau zwei Kommunikationspartnern** ausgetauscht.

Eine EGVP-Nachricht darf aus technisch-organisatorischen Gründen immer nur **genau ein Verfahren** des adressierten Gerichts oder der adressierten Staatsanwaltschaft betreffen. Dies gilt insbesondere auch für Schriftsätze in Klage- und Eilverfahren, die denselben Verfahrensgegenstand betreffen.

## 4.2 Adressierung

Für die Gerichte und Staatsanwaltschaften ist zur Kommunikation in gerichtlichen Verfahren, Ermittlungsverfahren und Bußgeldverfahren jeweils ein EGVP-Postfach eingerichtet.

Die EGVP-Postfächer sind im **EGVP-Verzeichnisdienst** (SAFE-Verzeichnisdienst) auffindbar. Sie wurden auf Grundlage der rechtlichen Vorgaben identifiziert.

### Kommunikationsmöglichkeiten

| Absender | Kann kommunizieren mit |
|----------|----------------------|
| **beA, beN, beSt, beBPo** | Justiz, eBO, MJP und untereinander |
| **eBO** | Justiz, beA, beN, beSt, beBPo (nicht mit anderen eBO/MJP) |
| **eBO-plus** | Zusätzlich auch untereinander |
| **MJP** | Justiz, beA, beN, beSt, beBPo (nicht mit anderen MJP/eBO) |

> **Hinweis:** Bußgeldbehörden verwenden für die Übermittlung von Nachrichten in Bußgeldsachen das beBPo.

## 4.3 Authentifizierung des Absenders

Jede EGVP-Nachricht enthält einen **vertrauenswürdigen Herkunftsnachweis (VHN)**, der Auskunft gibt, ob die Nachricht über einen bestimmten sicheren Übermittlungsweg übermittelt wurde. Er dient zur Authentifizierung der absendenden Person.

Der VHN ist eine **signierte Datei im XML-Format**. Die EGVP-Sende- und Empfangskomponenten prüfen den VHN beim Empfang automatisiert. Die Prüfergebnisse werden im PDF-Format bereitgestellt.

## 4.4 Nachweise zum Versand und Empfang

Für jede EGVP-Nachricht werden während des Übermittlungsprozesses automatisiert protokolliert:
- **Zeitpunkt des Eingangs**
- **Integrität der Nachricht** (unverändert?)
- **Sicherer Übermittlungsweg** (VHN-Prüfung)
- **Qualifizierte elektronische Signaturen** der Anhänge

### 4.4.1 Eingangszeitpunkt

Ein Dokument gilt als eingegangen, sobald es auf der für den Empfang bestimmten Einrichtung des Gerichts gespeichert ist (z.B. § 130a Abs. 5 ZPO).

In der EGVP-Infrastruktur bilden die **OSCI-Intermediäre** die für den Empfang bestimmten Einrichtungen. Es kommt **nicht** darauf an, dass die Nachricht vom Intermediär auch abgeholt wurde.

Protokolliert werden:
- Zeitpunkt des **Eingangs auf dem Intermediär**
- Zeitpunkt der **Abholung** vom Intermediär

### 4.4.2 Prüfergebnisse für empfangene Nachrichten

Nach dem Empfang wird automatisch geprüft:
- Integrität der Nachricht
- Verwendung eines sicheren Übermittlungswegs (VHN)
- Elektronische Signaturen der Anhänge

Die Ergebnisse werden in zwei Dokumenten bereitgestellt:

| Dokument | Inhalt | Format |
|----------|--------|--------|
| **Prüfvermerk** | Fachlich relevante Übermittlungsinformationen | PDF + XML |
| **Prüfprotokoll** | Zusätzliche technische Informationen | PDF + XML |

Beide enthalten Informationen zu:
- **Wer** – Inhaber des Absenderpostfaches
- **Was** – Hashwerte, Dateinamen, Signaturprüfergebnisse
- **Wann** – Zeitstempel des Eingangs
- **Wie** – Angaben zum Übermittlungsweg, Signaturen
- **An wen** – Empfängerpostfach

> **Empfehlung:** Den Prüfvermerk aufbewahren, da er als Nachweis der Übermittlung dient.

### 4.4.3 Nachweis für versendete Nachrichten

Nach dem Versand wird automatisch eine **Eingangsbestätigung** erstellt, die den Eingangszeitpunkt enthält. Diese kann zum Nachweis in den E-Akten-Systemen oder Fachverfahren gespeichert werden.

## 4.5 Größe der EGVP-Nachrichten und Anzahl der Anlagen

Die Anzahl und maximale Größe der Anlagen werden in der **ERV-Bekanntmachung (ERVB)** geregelt.

- Bei Überschreitung der Mengenbeschränkungen: ersatzweise Übermittlung auf einem **physischen Datenträger**
- Für Behördenakten nach BehAktÜbV: Grundsätzlich max. **200 MB** und **1.000 Anlagen** (Soll-Vorgabe)
- Größere Akten können gleichwohl übertragen werden und gelten als wirksam eingegangen, sofern die Übertragung möglich war

> **Hinweis:** Die Größenangaben beziehen sich auf die Summe der Größen der beigefügten Anlagen, nicht auf die Größe der EGVP-Nachricht selbst.

## 4.6 Kennzeichnung eiliger Nachrichten

Der XJustiz-Standard sieht im Nachrichtenkopf das Element **„Sendungspriorität"** vor:

| Wert | Bedeutung |
|------|-----------|
| 001 „Eilt" | Kennzeichnung im Regelbetrieb |
| Weitere Werte | Für Bereitschaftsdienste bei Gerichten und Staatsanwaltschaften |

Die Behandlung als eilig gekennzeichneter Nachrichten obliegt den Justizbehörden.

## 4.7 Übermittlung von Verschlusssachen

Die Komponenten der EGVP-Infrastruktur können derzeit **nicht** für den Versand von Verschlusssachen im Sinne der Verschlusssachenanweisungen genutzt werden.
