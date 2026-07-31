---
name: de-ahnenforschung-quellen
description: "DE-Quellenlogik: Sperrfristen, Kirchenbuch-Portale, Archiv-Zuständigkeiten für Deutschland."
category: de-ahnenforschung
version: 1.0.0
author: Schrauberhirn
license: MIT
platforms: [windows]
---

# DE-Ahnenforschung — Quellen (EBENE 2)

## Sperrfristen (Deutschland)

| Quelle | Sperrfrist |
|---|---|
| Standesamt Geburten | 110 Jahre |
| Standesamt Heiraten | 80 Jahre |
| Standesamt Todesurkunden | 30 Jahre |
| Kirchenbücher (ev./kath.) | 180 Jahre (vor 1876), danach 110 Jahre |

## DE-Kirchenbuch-Portale

### Matricula (katholisch)
- URL: matricula-online.eu
- Download-Workaround: Bilder auf `hosted-images.matricula-online.eu`
- Direkt-URL-Muster:
  `http://hosted-images.matricula-online.eu/images/matricula/DE-AEB/images/AEB_<ORT>/{num}_{ORT}_Bd.{X}_{K}/{num}_{ORT}_Bd.{X}_{K}_{BLATT}.jpg`
- Pausen von 0.12s zwischen Requests
- Bei 503/429: warten, nicht hämmern

### Archion (evangelisch)
- URL: archion.de
- Zugriff: Adobe-Pass (HTTP), kein Browser-Login
- API-Endpoint: `https://www.archion.de/api/v1/search`

### FamilySearch
- DE-Abdeckung: begrenzt (nur bestimmte Pfarreien)
- ToS: kein Bulk-Download
- WAF-Schutz bei API-Zugriff

## Konfessionelles Routing

| Religion | Archiv | Portal |
|---|---|---|
| römisch-katholisch | Bistumsarchiv | Matricula |
| evangelisch (luth.) | Landesarchiv | Archion |
| jüngst getauft | Gemeindearchiv | — |
| reformiert | Bundesarchiv | — |

## Landesarchive

| Bundesland | Archiv | Website |
|---|---|---|
| Bayern | Bayerisches Hauptstaatsarchiv | www.gda.bayern.de |
| Baden-Württemberg | Staatsarchiv | www.lubw.de |
| Nordrhein-Westfalen | Landesarchiv | www.la.nrw.de |
| Berlin | Staatsarchiv | www.staatsarchiv-berlin.de |

## Related
[[de-ahnenforschung-roadmap]]
[[de-ahnenforschung-kirchenbuecher]]