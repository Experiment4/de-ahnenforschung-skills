---
name: de-ahnenforschung-roadmap
description: "DE-Ahnenforschung Roadmap — Meta-Router & Skill-Kategorie für deutschlandfokussierte Ahnenforschung. DE-Quellen, Kirchenbücher, Stammbäume, DE-Geschichte."
category: de-ahnenforschung
version: 1.0.0
author: Schrauberhirn (NousResearch Discord), Hermes Agent
license: MIT
platforms: [windows, linux, macos]
metadata:
  hermes:
    tags: [Genealogy, Deutschland, DE-Quellen, Kirchenbücher, Stammbaum, Roadmap]
    related_skills:
      - de-ahnenforschung-daten
      - de-ahnenforschung-quellen
      - de-ahnenforschung-forschung
      - de-ahnenforschung-darstellung
      - de-ahnenforschung-verifikation
      - de-ahnenforschung-export
---

# DE-Ahnenforschung Roadmap (Deutschland-Fokus)

Deutschland-fokussierter Ahnenforschungs-Router. Ersetzt das generische `genealogy-roadmap` für deutsche Stammbäume.
Dieser Skill ist ein **META-ROUTER**: Er entscheidet, welcher Unter-Skill zu welchem Schritt gehört.
Er führt nichts selbst aus.

## Skill-Kategorien (EBENEN)

### EBENE 0 — Interpretation
- `de-ahnenforschung-interpretation`: Kurrent/Sütterlin/Latein-Glossar, Kirchenbuch-Status-Marker,
  Kirche→GEDCOM-Mapping, DE-Geschichte-Kontext (Stände, Territorien, Reichsstädte)

### EBENE 1 — Datenprozesse
- `de-ahnenforschung-daten`: Scans ablegen, Quellen erfassen, GEDCOM importieren,
  DE-Normalisierung (Umlaute, Reichsstadt-Namen, territoriale Zuordnungen),
  Windows-\r\n-Linebreak-Handling, RELI/PLAC-Tags aus Original-GEDCOM

### EBENE 2 — Forschungsprozesse (DE-Quellen-Logik)
- `de-ahnenforschung-quellen`: DE-spezifische Quellenlogik —
  **Hauptskill**. Sperrfristen (Standesamt 110/80/30 Jahre),
  Kirchenbuch-Portale (Matricula/Archion/FamilySearch),
  konfessionelles Routing (kath./ev./ reformiert),
  Archiv-Zuständigkeiten (Landesarchive, Staatsarchive),
  CompGen/Membrana/ANting,
  ToS-regeln für Bulk-Download
- `de-ahnenforschung-kirchenbuecher`: DE-Kirchenbuch-Portal-Praxis
  (UNTER-SKILL). Matricula-Arcanum-Workarounds,
  Pfarrei-Listen-Extraktion via PowerShell
- `de-ahnenforschung-transkription`: KI-Transkription (Kurrent/Sütterlin/Latein)
  via Gemini/Nous/OpenRouter → page_text + entry Tabellen
- `de-ahnenforschung-name`: Nachnamen-Forschung — Weltweite Verteilung
  (AGGREGAT, DSGVO-frei), Herkunft/Bedeutung, DE-Regionen (Geogen/DFDW)
- `de-ahnenforschung-agent-search`: Autonomer Such-Agent für DE-Quellen,
  Human-in-the-loop, review_queue mit Match-Score

### EBENE 3 — Ablage/Ergebnis
- `de-ahnenforschung-export`: GEDCOM 7.0 Export (Gramps-kompatibel),
  täglicher Review-Report an Discord/Telegram,
  DSGVO-konforme Ablage auf D:\Ahnenforschung,
  Backup in D:\backups

### EBENE 4 — Darstellung/Auswertung
- `de-ahnenforschung-darstellung`: Stammbaum, Nachkommen, Timeline,
  Geo-Map (DE-Migrationspfade), Quellen-Lücken-Analyse,
  Konfidenz-Dashboard, Forschungs-Queue
  Read-only auf db/working.sqlite

### QUERSCHNITT (keine EBENE)
- `de-ahnenforschung-verifikation`: Verification-Loop —
  technisch (DB-Integrität, DSGVO-Export-Leck, Quellen-Erreichbarkeit) +
  fachlich (GPS-5-Check, QUAY-Bewertung, Widerspruchs-Erkennung).
  Läuft nach data-capture-Accept und vor tree-archive-Export
- `de-ahnenforschung-geschichte`: DE-Geschichte-Kontext —
  Territorialentwicklung (Deutsches Reich, DDR, Länder),
  Konfessionsgeschichte (Reformation, Gegenreformation),
  Standesrecht, Einwohnsklauseln

## Routing-Entscheidungshilfe

| Was soll ich tun? | Skill laden |
|---|---|
| Scans ablegen + normalisieren | de-ahnenforschung-daten |
| Original-GEDCOM lesen | de-ahnenforschung-daten |
| Kirchenbuch-Scan transkribieren | de-ahnenforschung-transkription |
| Kurrent/Sütterlin lesen lernen | de-ahnenforschung-interpretation |
| Standesamt-Bestellung | de-ahnenforschung-quellen |
| Matricula/Archion durchsuchen | de-ahnenforschung-kirchenbuecher |
| Nachname forschen | de-ahnenforschung-name |
| Datenbank prüfen | de-ahnenforschung-verifikation |
| Stammbaum ansehen | de-ahnenforschung-darstellung |
| Exportieren | de-ahnenforschung-export |
| Hintergrund: Preußen/DDR/Territorien | de-ahnenforschung-geschichte |

## Connected
[[de-ahnenforschung-daten]]
[[de-ahnenforschung-quellen]]
[[de-ahnenforschung-interpretation]]