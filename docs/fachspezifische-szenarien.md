# Fachspezifische Kommunikationsszenarien

## Mahnverfahren

Im Automatisierten Mahnverfahren wird unterschieden zwischen:

- **a)** Maschinell lesbare Daten nach § 702 Abs. 2 S. 1 ZPO
- **b)** Andere Anträge, Schriftsätze usw.

Für **maschinell lesbare Daten (a)** gelten besondere Formate gemäß der „Konditionen zur Teilnahme am elektronischen Datenaustausch" (siehe [mahngerichte.de](https://www.mahngerichte.de/publikationen/eda-konditionen/)). Eine physische Antragsdatei kann bis zu **32.768 logische Anträge** enthalten. Die ERVV gilt hierfür nicht.

Für alle **anderen Anträge und Schriftsätze (b)** gelten die allgemeinen Regeln des ERV.

## Bußgeldverfahren

Die Bußgeldbehörden verwenden das **besondere Behördenpostfach (beBPo)**. Für die Übermittlung strukturierter Daten stehen gesonderte XJustiz-Nachrichten zur Verfügung.

Fachliche Rahmenbedingungen sind in der [Anlage (Kapitel 9)](bussgeldverfahren.md) zusammengetragen.

### Kommunikation von der Bußgeldbehörde zur Justiz

| Nr. | Kommunikationsanlass | XJustiz-Nachricht | Ereignis |
|-----|---------------------|-------------------|----------|
| BBJ1 | Rechtsbehelfsabgabe (§ 69 Abs. 3 OWiG) | `verfahrensmitteilung.externAnJustiz.0500010` | 116, Neueingang OWi |
| BBJ2 | Abgabe als Straftat (§ 41 OWiG) | `verfahrensmitteilung.externAnJustiz.0500010` | 115, Neueingang |
| BBJ3 | Antrag auf gerichtliche Entscheidung (z. B. § 25a StVG) | `verfahrensmitteilung.externAnJustiz.0500010` | 115, Neueingang |
| BBJ4 | Antrag auf Erzwingungshaft (§ 96 OWiG) | `verfahrensmitteilung.externAnJustiz.0500010` | 117, Neueingang E-Haft |
| BBJ5 | Anträge nach § 98 OWiG (Umwandlung Geldbuße) | `verfahrensmitteilung.externAnJustiz.0500010` | 115, Neueingang |
| BBJ6 | Nachträgliche Zahlungsmitteilungen | `verfahrensmitteilung.externAnJustiz.0500010` | 121, Nachträgliche Mitteilung |
| BBJ7 | Stornierung zu Zahlungsmitteilungen | `verfahrensmitteilung.externAnJustiz.0500010` | 121, Nachträgliche Mitteilung |
| BBJ8 | Nachträgliche Rücknahme | `verfahrensmitteilung.externAnJustiz.0500010` | 215, Rücknahme Antrag/Schreiben |
| BBJ9 | Aktenzeichenmitteilung | `aktenzeichenmitteilung.0500002` | – |
| BBJ10 | Übermittlung von Dokumenten | `uebermittlungSchriftgutobjekte.0005005` | – |

### Kommunikation von der Justiz zur Bußgeldbehörde

| Nr. | Kommunikationsanlass | XJustiz-Nachricht | Ereignis |
|-----|---------------------|-------------------|----------|
| JBB1 | Aktenabgabe | `verfahrensmitteilung.externAnJustiz.0500010` | 141, Aktenabgabe |
| JBB2 | Mitteilung Verfahrensausgang (Einspruch mit gerichtl. Entscheidung) | `verfahrensmitteilung.justizAnExtern.0500011` | 034, Ergebnismitteilung |
| JBB3 | Mitteilung Verfahrensausgang (Einstellung/Rücknahme/Tod) | `verfahrensmitteilung.justizAnExtern.0500011` | 034, Ergebnismitteilung |
| JBB4 | Verfahrensausgangsmitteilung (Erzwingungshaft/§ 98 OWiG) | `verfahrensmitteilung.justizAnExtern.0500011` | 034, Ergebnismitteilung |
| JBB5 | Übermittlung von Dokumenten | `uebermittlungSchriftgutobjekte.0005005` | – |
| JBB6 | Aktenzeichenmitteilung | `aktenzeichenmitteilung.0500002` | – |

## Handels-, Genossenschafts- und Partnerschaftsregistersachen

In diesen Registersachen gelten **nicht die allgemeinen Vorschriften**, insbesondere nicht die ERVV. Die in den einzelnen Bundesländern erlassenen Rechtsverordnungen sind vorrangig zu beachten.

Eine Übersicht der Verordnungen führt die Bundesnotarkammer unter [elrv.info](https://www.elrv.info/elektronischer-rechtsverkehr/uebersicht-verordnungen).

## Zentrales Schutzschriftenregister

Eine gültige Einreichung besteht mindestens aus:

- **Primärdokument** – das Schutzschriftendokument in einem zugelassenen Format
- **XJustiz-Datensatz** – für die automatische Datenverarbeitung

!!! warning "Hinweis"
    Der über beA erzeugbare XJustiz-Datensatz ist für das Schutzschriftenregister **nicht gültig**.

**Zugelassene Dateiformate:**

1. PDF und PDF/A (`.pdf`)
2. Rich Text Format (`.rtf`)
3. Microsoft Word ohne Makros (`.doc`, `.docx`)
4. XML (`.xml`)

Ein Dokumentenschutz darf **nicht** angebracht werden.

## Zentrales Vollstreckungsgericht

Das Schuldnerverzeichnis (§ 882h ZPO) und das Vermögensverzeichnis (§ 802k ZPO) werden über [vollstreckungsportal.de](https://www.vollstreckungsportal.de) geführt.

- Einlieferung erfolgt über **EGVP** durch Gerichtsvollzieher, Stadtkassen, Finanzämter, Hauptzollämter
- Daten als einheitlich strukturierte **XJustiz-Datensätze** im XML-Format
- Jeder Datensatz wird **einzeln** übermittelt
- Verarbeitung wird mit einer **Quittungsnachricht** bestätigt

## Schiffsregistersachen

In Schiffsregistersachen gelten vorrangig die in den einzelnen Bundesländern gemäß § 94 Abs. 1 S. 2 der Schiffsregisterordnung erlassenen Rechtsverordnungen.

## Zwangsvollstreckung

Ab XJustiz-Version 3.5.1 steht ein **Fachmodul „Zwangsvollstreckung"** bereit.

!!! info "Aktueller Stand"
    Die Übermittlung von Zwangsvollstreckungsanträgen in ausschließlich strukturierter Form ist **noch nicht gesetzlich geregelt**. Vollstreckungsformulare sind daher im **PDF-Format** einzureichen. Ab XJustiz 3.5 sollen zusätzlich strukturierte Daten übermittelt werden.

Beteiligte, die das Fachmodul noch nicht umgesetzt haben, verwenden die allgemeine Nachricht `nachricht.gds.uebermittlungSchriftgutobjekte.0005005`.
