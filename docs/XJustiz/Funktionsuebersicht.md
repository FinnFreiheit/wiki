# Funktionsübersicht der XJustiz-Werkzeuge

Die folgende Übersicht zeigt alle verfügbaren Module, deren Funktionen und den aktuellen Bereitstellungsstand.

=== "Validator"

    | Funktion | Beschreibung | Version | Demo |
    |----------|--------------|---------|------|
    | Validierung der XJustiz-Nachricht | Der Validator prüft die Konformität einer XJustiz-Nachricht zu den Standardvorgaben und stellt einen Validierungsreport bereit. | initial | ja |

=== "Konverter"

    **PDF-Konvertierung**

    | Funktion | Beschreibung | Version | Demo |
    |----------|--------------|---------|------|
    | `nachricht.gds.basisnachricht.0005006` | Konvertierung der XJustiz-Nachrichten in ausgefüllte PDF-Formulare | 0.3.0 | ja |
    | `nachricht.straf.bfj.benachrichtigung.0500650` | | | ja |
    | `nachricht.straf.bfj.bzr.auskunftserteilung.auskunft.0500102` | | | ja |
    | `nachricht.straf.bfj.bzr.auskunftserteilung.auslandsnachricht.0500103` | | | ja |
    | `nachricht.straf.bfj.bzr.auskunftserteilung.fuehrungszeugnisAuskunft.0500105` | | | ja |
    | `nachricht.straf.bfj.bzr.hinweis.0500301` | | | ja |
    | `nachricht.straf.bfj.gzr.auskunftserteilung.auskunft.0500402` | | | ja |
    | `nachricht.straf.fehlermitteilung.0500019` | | | ja |
    | `nachricht.zvstr.forderungspfaendung.2600002` | ANTRAG, BESCHLUSS, FORDERUNG | | ja |
    | eEB | | 0.5.0 | nein |

    **Format-Konvertierung**

    | Funktion | Beschreibung | Version | Demo |
    |----------|--------------|---------|------|
    | Xdomea zu XJustiz | Aus einer XDomea-Nachricht und einer XJustiz-Nachricht ohne Schriftgutobjekt wird eine XJustiz-Nachricht mit den übertragenen Inhalten erzeugt. Eingabeformular zur Angabe der benötigten XJustiz-Informationen vorhanden. | initial | ja |
    | Konvertierung zwischen XJustiz-Versionen | XJustiz-Nachrichten werden in eine andere Version konvertiert, sofern das möglich ist. | initial | nein |

=== "Formularsammlung"

    | Funktion | Beschreibung | Version | Demo |
    |----------|--------------|---------|------|
    | Mitteilung von Zahlungseingängen | Formular von elektronischen Mitteilungen von Zahlungseingängen im OWI-Verfahren | 0.6.0 | ja |
    | Einspruchsabgabe | Formular für die elektronische Abgabe von Einsprüchen im OWI-Verfahren | 0.6.0 | ja |
    | ERV Strukturdatensatz | | 1.0.0 | nein |

=== "Generator"

    | Funktion | Beschreibung | Version | Demo |
    |----------|--------------|---------|------|
    | `basis_sgo` | Aus einer JSON-Datei gemäß bereitgestellter OpenAPI-Schema-Dokumentation wird eine der entsprechenden XJustiz-Nachrichten erzeugt. Die Generierung der JSON erfolgt in der Anwendung. | initial | nein |
    | `nachrichtStrafOwiVerfahrensmitteilungExternAnJustiz0500010` | | | nein |
    | `nachrichtStrafOwiVerfahrensmitteilungJustizAnExtern0500011` | | | nein |
    | `nachricht.enova.entscheidung.2900003` | | | nein |
    | `nachricht.enova.mitteilung.2900004` | | | nein |
    | eEB | | initial | nein |
