# 4. Übermittlung der Nachrichten

Der Austausch von Dokumenten, Akten und strukturierten, maschinenlesbaren Datensätzen auf einem sicheren Übermittlungsweg erfolgt über die Infrastruktur des EGVP unter Verwendung des beA, beN, beSt, beBPo, eBO oder des MJP.

## 4.1 Beteiligte Kommunikationspartner

Eine EGVP-Nachricht wird immer zwischen **genau zwei Kommunikationspartnern** ausgetauscht.

!!! warning "Wichtig"
    Eine EGVP-Nachricht darf aus technisch-organisatorischen Gründen immer nur **genau ein Verfahren** des adressierten Gerichts oder der adressierten Staatsanwaltschaft betreffen. Dies gilt insbesondere auch für das Einreichen von Schriftsätzen in Klage- und Eilverfahren, die denselben Verfahrensgegenstand betreffen.

### Kommunikationsmöglichkeiten

| Von / An | Justiz | beA, beN, beSt | beBPo | eBO | MJP |
|----------|--------|----------------|-------|-----|-----|
| **Justiz** | – | ✅ | ✅ | ✅ | ✅ |
| **beA, beN, beSt** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **beBPo** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **eBO** | ✅ | ✅ | ✅ | ❌¹ | ❌ |
| **MJP** | ✅ | ✅ | ✅ | ❌ | ❌ |

¹ eBO-plus-Inhaber können auch untereinander kommunizieren.

Für die Ausstattung der professionellen Einreicher mit einem beA, beN oder beSt sind die jeweiligen berufsständischen Kammern zuständig.

## 4.2 Adressierung

Für die Gerichte und Staatsanwaltschaften ist zur Kommunikation in gerichtlichen Verfahren, Ermittlungsverfahren und Bußgeldverfahren jeweils ein EGVP-Postfach eingerichtet.

Die EGVP-Postfächer der Justiz und der Inhaber der besonderen Postfächer sind im **EGVP-Verzeichnisdienst** (auch SAFE-Verzeichnisdienst) auffindbar. Sie wurden auf Grundlage der rechtlichen Vorgaben identifiziert.

Die Bußgeldbehörden verwenden für die Übermittlung von Nachrichten in Bußgeldsachen das **besondere Behördenpostfach (beBPo)**, das für die Behörde eingerichtet wurde.

## 4.3 Authentifizierung des Absenders

Jede EGVP-Nachricht enthält einen **vertrauenswürdigen Herkunftsnachweis (VHN)**, der Auskunft darüber gibt, ob die Nachricht über einen bestimmten sicheren Übermittlungsweg übermittelt wurde. Der VHN ist eine signierte Datei im XML-Format.

Die EGVP-Sende- und Empfangskomponenten prüfen den VHN beim Empfang automatisiert. Die Prüfergebnisse werden protokolliert und im PDF-Format bereitgestellt. Es besteht deshalb **keine Notwendigkeit**, die strukturierten Daten des VHN gesondert auszuwerten.

## 4.4 Nachweise zum Versand und Empfang

Für jede EGVP-Nachricht werden während des Übermittlungsprozesses bestimmte Informationen automatisiert protokolliert, insbesondere der Zeitpunkt des Eingangs.

### 4.4.1 Eingangszeitpunkt

Gemäß den gesetzlichen Vorschriften (z. B. § 130a Abs. 5 ZPO) gilt ein Dokument als eingegangen, sobald es auf der für den Empfang bestimmten Einrichtung des Gerichts gespeichert ist.

In der EGVP-Infrastruktur bilden die sogenannten **OSCI-Intermediäre** die für den Empfang bestimmten Einrichtungen. Ein Dokument gilt als eingegangen, wenn die zugehörige Nachricht auf dem OSCI-Intermediär des Empfängers eingegangen ist. **Es kommt nicht darauf an, dass die Nachricht vom Intermediär auch abgeholt wurde.**

### 4.4.2 Prüfergebnisse für empfangene Nachrichten

Nach dem Empfang wird automatisch geprüft:

- ob die Nachricht **integer** ist
- ob ein **sicherer Übermittlungsweg** verwendet wurde (Prüfung des VHN)
- alle **elektronischen Signaturen** der beigefügten Anhänge

Die Ergebnisse werden in zwei Dokumente übernommen:

| Dokument | Inhalt |
|----------|--------|
| **Prüfvermerk** | Alle fachlich relevanten Informationen zur Übermittlung |
| **Prüfprotokoll** | Fachliche Informationen + weitere technische Informationen |

!!! tip "Empfehlung"
    Der Prüfvermerk sollte aufbewahrt werden, da er als Nachweis der Übermittlung dient.

Der Prüfvermerk und das Prüfprotokoll enthalten Informationen darüber:

- **Wer** – Inhaber des Absenderpostfaches
- **Was** – Hashwerte der beigefügten Dateien, Dateinamen, Prüfergebnisse
- **Wann** – Zeitstempel des Eingangs
- **Wie** – Angaben zum sicheren Übermittlungsweg, signierte Dokumente
- **An wen** – Empfängerpostfach

### 4.4.3 Nachweis für versendete Nachrichten

Nach dem Versand wird automatisch eine **Eingangsbestätigung** erstellt, die den Eingangszeitpunkt enthält. Diese kann zum Nachweis des Eingangs in den E-Akten-Systemen oder Fachverfahren gespeichert werden.

## 4.5 Größe der EGVP-Nachrichten und Anzahl der Anlagen

Die Anzahl und maximale Größe der Anlagen werden in der **ERV-Bekanntmachung (ERVB)** geregelt.

!!! info "Grenzwerte"
    Grundsätzlich sollen Nachrichten eine Größe von **200 MB** und **1.000 Anlagen** nicht überschreiten.

Sofern die Größe oder Anzahl die Beschränkungen überschreiten, können sie ersatzweise auf einem **physischen Datenträger** an das Gericht übermittelt werden.

Für die Übermittlung elektronischer Akten gilt die **Behördenaktenübermittlungsverordnung (BehAktÜbV)**. Akten, die größer als 200 MB sind, können gleichwohl übertragen werden und gelten – sofern die Übertragung möglich war – als wirksam eingegangen.

## 4.6 Kennzeichnung eiliger Nachrichten

Der XJustiz-Standard sieht eine Werteliste (Nachrichtenkopf, Element „Sendungspriorität") vor:

- **Wert 001 „Eilt"** – für Nachrichten im Regelbetrieb
- Spezielle Werte – für Bereitschaftsdienste bei Gerichten und Staatsanwaltschaften

Die Behandlung als eilig gekennzeichneter Nachrichten obliegt den Justizbehörden.

## 4.7 Übermittlung von Verschlusssachen

!!! danger "Nicht möglich"
    Die Komponenten der EGVP-Infrastruktur können derzeit **nicht** für den Versand von Verschlusssachen im Sinne der Verschlusssachenanweisungen genutzt werden.
