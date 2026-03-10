---
layout: home
title: Startseite
---

# Elektronischer Rechtsverkehr

Willkommen im Wiki zum **Elektronischen Rechtsverkehr** (ERV) mit der Justiz.

Dieses Wiki basiert auf dem **Leitfaden der Arbeitsgruppe „IT-Standards in der Justiz"** der Bund-Länder-Kommission für Informationstechnik in der Justiz (Version 1.6, Stand 28.07.2025).

Der ERV ermöglicht Bürgern, Behörden, Organisationen sowie professionellen Einreichern (Rechtsanwälte, Notare, Steuerberater, Gerichtsvollzieher) den sicheren und rechtlich wirksamen Austausch elektronischer Dokumente und Akten mit der Justiz.

## Inhalte

{% for page in site.pages %}{% if page.layout == 'page' %}
- [{{ page.title }}]({{ page.url | relative_url }})
{% endif %}{% endfor %}
