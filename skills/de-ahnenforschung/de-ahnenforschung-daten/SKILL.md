---
name: de-ahnenforschung-daten
description: "DE-Ahnenforschung Daten: Scans ablegen, Quellen erfassen, GEDCOM importieren, DE-Normalisierung."
category: de-ahnenforschung
version: 1.0.0
author: Schrauberhirn
license: MIT
platforms: [windows]
---

# DE-Ahnenforschung — Daten (EBENE 1)

Erfassung und Normalisierung von Ahnenforschungsdaten für **Deutschland**.

## Verzeichnislayout (D:\Ahnenforschung\)

- `gedcom/` — Original-GEDCOM-Files (QUELLE DER WAHRHEIT)
- `db/working.sqlite` — Arbeitsdatenbank
- `docs/` — Scans/Urkunden
- `reports/` — Chart-Exporte (HTML+PNG)
- `images/` — Ahnen-Bilder
- `cache/` — Transkriptions-Cache
- `pool/` — Rohdaten-Imports

## DE-Normalisierung

### Umlaute
```
ue → ü, ae → ä, oe → ö, ss → ß
Groß-/Kleinschreibung bewahren
```

### Historische Territorien
| Historisch | Modern |
|---|---|
| Preußen | Brandenburg, Mecklenburg-Vorpommern, etc. |
| Ostdeutschland | Polen, Tschechien, Rumänien |
| Schlesien | Polen, Tschechien |
| Pommern | Deutschland, Polen |

### Windows \r\n Linebreaks
Immer `f.read().splitlines()` verwenden, NICHT `split("\n")`.

## confidence-Konvention
- `belegt` — Primärquelle (Kirchenbuch, Standesamt)
- `unbestaetigt` — Sekundärquelle (OFB, Index)
- `Vermutung` — Geraten, keine Quelle

## Verzeichnisstruktur
```
D:\Ahnenforschung\
├── gedcom\          # Original GEDCOM
├── db\working.sqlite
├── docs\            # Scans
├── reports\         # Exporte
├── images\          # Fotos
├── cache\           # Transkription
└── pool\            # Imports
```

## Related
[[de-ahnenforschung-roadmap]]
[[de-ahnenforschung-interpretation]]