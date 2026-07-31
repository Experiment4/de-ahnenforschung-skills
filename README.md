# DE-Ahnenforschung Skills

Deutschland-fokussierter Ahnenforschungs-Skill-Set für **Hermes Agent** (kann auch für andere adaptiert werden)
Dieses Skill-Set bietet komplette deutschlandfokussierte Ahnenforschung für Hermes Agent. 
Alle 9 Skills sind auf Deutsch verfasst und gezielt auf deutsche Quellen zugeschnitten.
Die skills sind entlang wissenschaftlicher Arbeitsweise aufgebaut und unterstützen Grundlagen und Kontextnachforschungen. Beispiel: Veränderung der Regierungsformen, Schreibweisen, Schriftarten

EBENE 0 (Interpretation):
  Unterstützung bei Kurrent/Sütterlin-Handschriften
  Latein-Glossar und Kirchenbuch-Glossar. Ideal für historische Dokumente.
EBENE 1 (Daten): 
  Erfassung und Normalisierung von Scans
  GEDCOM-Import mit Umlaut-Bereinigung und deutscher Zeichensatzbehandlung (UTF-8).
EBENE 2 (Quellen): Spezialisiert auf deutsche Archive 
  Standesamt-Sperrfristen (110/80/30 Jahre)
  Matricula/Archion-Anbindung für katholische und evangelische Kirchenbücher
  DFW/CompGen-Integration. 
  Enthält Downloads-Automation für Matricula-Bilder.
EBENE 3 (Export):
  GEDCOM 7.0-Export
  tägliche Review-Reports an Discord/Telegram
  DSGVO-konforme Ablage
  automatisierte Backups
EBENE 4 (Darstellung): 
  Interaktive Stammbaum-Dashboards mit Timeline, Geo-Karten und Konfidenz-Anzeige (grün=belegt, gelb=vermutet) auf Deutsch !

Querschnitts-Skills: 
GPS-5-Check für wissenschaftliche Standardsicherheit und Verifikation aller Fakten. 
DE-Geschichte-Kontext für Territorialwechsel von Preußen/DDR/Bundesrepublik.

Perfekt für Forschung in Bayern, Baden-Württemberg, NRW, Berlin und anderen deutschen Regionen.

## Installation

Dieses Skill-Set kann über den Hermes SkillHub installiert werden:

```
hermes skills install --from de-ahnenforschung
```

Oder manuell:
```bash
# Clone das Repository
git clone https://github.com/Schrauberhirn/de-ahnenforschung-skills.git
cp -r de-ahnenforschung-skills/skills/de-ahnenforschung ~/.hermes/profiles/werkstatt/skills/

# In Hermes neu laden
hermes dev skills --reload
```

## Skills (9)

| Skill | EBENE | Fokus |
|---|---|---|
| `de-ahnenforschung-roadmap` | Meta | Router — legt fest welcher Skill wann |
| `de-ahnenforschung-daten` | 1 | Datenimport, DE-Normalisierung, GEDCOM |
| `de-ahnenforschung-quellen` | 2 | DE-Quellenlogik, Sperrfristen, Archive |
| `de-ahnenforschung-kirchenbuecher` | 2 | Matricula/Archion/FamilySearch |
| `de-ahnenforschung-interpretation` | 0 | Kurrent/Sütterlin/Latein |
| `de-ahnenforschung-darstellung` | 4 | Stammbaum Dashboard (HTML) |
| `de-ahnenforschung-verifikation` | Querschnitt | GPS-5-Check, DSGVO |
| `de-ahnenforschung-export` | 3 | GEDCOM 7.0, Review-Report |
| `de-ahnenforschung-geschichte` | Kontext | Territorialentwicklung, Konfession |

## Lizenz

MIT — siehe [LICENSE](LICENSE)
