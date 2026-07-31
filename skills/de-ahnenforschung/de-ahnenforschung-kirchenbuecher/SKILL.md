---
name: de-ahnenforschung-kirchenbuecher
description: "DE-Kirchenbuch-Portale: Matricula/Archion/FamilySearch Zugriff und Download-Strategien."
category: de-ahnenforschung
version: 1.0.0
author: Schrauberhirn
license: MIT
platforms: [windows]
---

# DE-Ahnenforschung — Kirchenbücher (UNTER-SKILL von Quellen)

## Matricula (katholisch)

### Direct Image URL Pattern (Schnaittach)
```
http://hosted-images.matricula-online.eu/images/matricula/DE-AEB/images/AEB_Schnaittach/
{num:04d}_Schnaittach_Bd.{X}_{K}/{num:04d}_Schnaittach_Bd.{X}_{K}_{BLATT}.jpg
```

### Parameter
- `num` = fortlaufende Bandnummer (Basis + Kapitel)
- `BLATT` = 0000–0012 (404 = Ende)
- Download-Pause: 0.12s pro Bild
- Cache: `_num_basis_cache.json` pro Pfarrei

### Schritte
1. Pfarrei-Ordner anlegen: `sources/matricula/<pfarrei>/M{X}_{Y}/`
2. `download_matricula_full.py` ausführen
3. Dateinamen: `K{KAPITEL}_{BLATT}.jpg`

## Archion (evangelisch)

### Zugriff
- Adobe-Pass (HTTP-basiert)
- API-Endpoint: `https://www.archion.de/api/v1/search`
- Kein Browser-Login nötig

## FamilySearch

### DE-Abdeckung
Begrenzt — nur bestimmte Pfarreien indexiert.
- WAF-Schutz aktiv
- Rate-Limit: 100 Requests/Tag

## Related
[[de-ahnenforschung-quellen]]
[[de-ahnenforschung-roadmap]]