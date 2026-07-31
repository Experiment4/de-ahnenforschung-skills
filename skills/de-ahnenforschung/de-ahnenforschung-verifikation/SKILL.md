---
name: de-ahnenforschung-verifikation
description: "DE-Verifikation: DB-Integrität, DSGVO-Export-Leck, GPS-5-Check, QUAY-Bewertung."
category: de-ahnenforschung
version: 1.0.0
author: Schrauberhirn
license: MIT
platforms: [windows]
---

# DE-Ahnenforschung — Verifikation (QUERSCHNITT)

## Verification-Loop

### 1. Technisch
- **DB-Integrität**: Foreign-Key-Checks (`person.family_id → family.id`)
- **DSGVO-Export-Leck**: `SELECT * FROM person WHERE name ILIKE '%lebend%'`
- **Quellen-Erreichbarkeit**: HTTP-Status-Codes für Kirchenbuch-Links

### 2. Fachlich
- **GPS-5-Check** (Genealogische Standard-Protokoll):
  1. Anschaulichkeitsgrad (Clarity)
  2. Gegendarstellung (Conflict resolution)
  3. Mehrere Quellen (Multiple sources)
  4. Primärquellen (Primary sources)
  5. unabhängige Quellen (Independent sources)
- **QUAY-Bewertung** (GEDCOM-Qualität):
  - 0 = unsicher (Vermutung)
  - 1 = sekundär (unbestaetigt)
  - 2 = primär (belegt)
  - 3 = Sekundär + Primär
  - 4 = Primär + Sekundär + unabhängig

## confidence-Konvention (DE)

| Wert | Bedeutung | QUAY |
|---|---|---|
| belegt | Primärquelle (Kirchenbuch, Standesamt) | 2 |
| unbestaetigt | Sekundärquelle (OFB, Index) | 1 |
| Vermutung | Geraten, keine Quelle | 0 |

## Related
[[de-ahnenforschung-roadmap]]
[[de-ahnenforschung-daten]]