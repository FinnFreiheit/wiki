---
layout: page
title: 8 – Fachspezifische Szenarien
nav_order: 8
---

# Fachspezifische Kommunikationsszenarien

## 8.1 Mahnverfahren

Im Automatisierten Mahnverfahren wird unterschieden zwischen:

**a) Maschinell lesbare Daten** (§ 702 Abs. 2 S. 1 ZPO)
- Besondere Formate gemäß den „Konditionen zur Teilnahme am elektronischen Datenaustausch" ([mahngerichte.de](https://www.mahngerichte.de/publikationen/eda-konditionen/))
- Eine physische Antragsdatei kann bis zu **32.768 logische Anträge** enthalten
- Die ERVV gilt hier **nicht**

**b) Andere Anträge, Schriftsätze**
- Es gelten die allgemeinen Regeln des ERV

## 8.2 Bußgeldverfahren

Die Bußgeldbehörden verwenden das **beBPo** für die Übermittlung. Für strukturierte Daten stehen **gesonderte XJustiz-Nachrichten** zur Verfügung.

### Vorgaben bei Übergang der Aktenführungsbefugnis

| Von → An | Inhalt der Übermittlung |
|----------|----------------------|
| Justiz → Bußgeldbehörde | Akte mit Ursprungsdateien, Signaturdateien, PDF-Repräsentate, Signaturprüfergebnisse |
| Ohne Übergang der Aktenführung | Mindestens PDF-Repräsentate |
| Bußgeldbehörde → Justiz | Selbsterstellte Dokumente im **PDF/A-Format**, ggf. Ausgangsformat zusätzlich |
| Dokumente Dritter | PDF/A + bei Aktenführungsübergang auch Ausgangsdokument mit Signaturdateien |

### 8.2.1 Kommunikation von der Bußgeldbehörde zur Justiz

| Nr. | Kommunikationsanlass | XJustiz-Nachricht | Ereignis |
|-----|---------------------|-------------------|----------|
| BBJ1 | Rechtsbehelfsabgabe (§ 69 Abs. 3 OWiG) | `verfahrensmitteilung.externAnJustiz.0500010` | 116, Neueingang OWi |
| BBJ2 | Abgabe als Straftat (§ 41 OWiG) | `verfahrensmitteilung.externAnJustiz.0500010` | 115, Neueingang |
| BBJ3 | Antrag auf gerichtliche Entscheidung (z.B. § 25a StVG) | `verfahrensmitteilung.externAnJustiz.0500010` | 115, Neueingang |
| BBJ4 | Antrag auf Erzwingungshaft (§ 96 OWiG) | `verfahrensmitteilung.externAnJustiz.0500010` | 117, Neueingang E-Haft |
| BBJ5 | Anträge nach § 98 OWiG (Umwandlung Geldbuße) | `verfahrensmitteilung.externAnJustiz.0500010` | 115, Neueingang |
| BBJ6 | Nachträgliche Zahlungsmitteilungen | `verfahrensmitteilung.externAnJustiz.0500010` | 121, Nachträgliche Mitteilung |
| BBJ7 | Nachträgliche Stornierungen | `verfahrensmitteilung.externAnJustiz.0500010` | 121, Nachträgliche Mitteilung |
| BBJ8 | Nachträgliche Rücknahme | `verfahrensmitteilung.externAnJustiz.0500010` | 215, Rücknahme Antrag/Schreiben |
| BBJ9 | Aktenzeichenmitteilung | `aktenzeichenmitteilung.0500002` | – |
| BBJ10 | Übermittlung von Dokumenten | `uebermittlungSchriftgutobjekte.0005005` | – |

### 8.2.2 Kommunikation von der Justiz zur Bußgeldbehörde

| Nr. | Kommunikationsanlass | XJustiz-Nachricht | Ereignis |
|-----|---------------------|-------------------|----------|
| JBB1 | Aktenabgabe (§ 43 OWiG) | `verfahrensmitteilung.externAnJustiz.0500010` | 141, Aktenabgabe |
| JBB2 | Verfahrensausgang bei Einspruch mit gerichtlicher Entscheidung | `verfahrensmitteilung.justizAnExtern.0500011` | 034, Ergebnismitteilung |
| JBB3 | Verfahrensausgang nach Einstellung/Rücknahme/Tod | `verfahrensmitteilung.justizAnExtern.0500011` | 034, Ergebnismitteilung |
| JBB4 | Verfahrensausgang bei Erzwingungshaft / § 98 OWiG | `verfahrensmitteilung.justizAnExtern.0500011` | 034, Ergebnismitteilung |
| JBB5 | Übermittlung von Dokumenten | `uebermittlungSchriftgutobjekte.0005005` | – |
| JBB6 | Aktenzeichenmitteilung | `aktenzeichenmitteilung.0500002` | – |

## 8.3 Handels-, Genossenschafts- und Partnerschaftsregistersachen

Hier gelten **nicht die allgemeinen Vorschriften** (insbesondere nicht die ERVV). Vorrangig sind die in den einzelnen Bundesländern erlassenen Rechtsverordnungen.

Übersicht der Verordnungen: [elrv.info](https://www.elrv.info/elektronischer-rechtsverkehr/uebersicht-verordnungen)

## 8.4 Zentrales Schutzschriftenregister

- Maschinell lesbarer Datensatz nach §§ 1, 2 SRV erforderlich
- Mindestangaben nach § 1 Abs. 2 Nr. 1 und 2
- XJustiz-Datensatz muss `xjustiz_nachricht.xml` heißen
- Der über beA erzeugbare XJustiz-Datensatz ist hier **nicht gültig**

**Zulässige Dateiformate:**
- PDF und PDF/A (.pdf)
- Rich Text Format (.rtf)
- Microsoft Word ohne Makros (.doc, .docx)
- XML (.xml)

> Kein Dokumentenschutz erlaubt.

## 8.5 Zentrales Vollstreckungsgericht

- Schuldnerverzeichnis (§ 882h ZPO) und Vermögensverzeichnis (§ 802k ZPO)
- Zentral pro Land geführt, länderübergreifend über [vollstreckungsportal.de](https://www.vollstreckungsportal.de) einsehbar
- Einlieferung über EGVP als XJustiz-XML-Datei
- Jeder Datensatz wird **einzeln** übermittelt und mit einer **Quittungsnachricht** bestätigt
- Bei Abweisung: Fehlercode mit Grund

## 8.6 Schiffsregistersachen

Für Seeschiffs-, Binnenschiffs- und Schiffsbauregister gelten vorrangig die Rechtsverordnungen der einzelnen Bundesländer (§ 94 Abs. 1 S. 2 Schiffsregisterordnung).

## 8.7 Zwangsvollstreckung

- Ab **XJustiz-Version 3.5.1**: Fachmodul „Zwangsvollstreckung"
- Vollstreckungsformulare sind im **PDF-Format** einzureichen
- Ab XJustiz 3.5: **zusätzlich** als strukturierte Daten im XJustiz-Format übermitteln
- Ohne Fachmodul: PDF + allgemeine Nachricht `uebermittlungSchriftgutobjekte.0005005`
