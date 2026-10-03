---
name: de-ahnenforschung-verifikation
description: Use when du newly akzeptierte Personen prüfen möchtest. Führt technischen (Integrität, DSGVO) und fachlichen (GPS‑5, QUAY, Widerspruchs‑Erkennung) Verification‑Loop aus.
category: de-ahnenforschung
version: 1.0.0
author: Schrauberhirn (NousResearch Discord), Hermes Agent
license: MIT
platforms:
- windows
- linux
- macos
metadata:
  hermes:
    tags:
    - Verification
    - Genealogy
    related_skills:
    - genealogy-shared
---

# genealogy-verification (Verification-Loop)

QUERSCHNITT. Prüft Forschungsergebnisse auf zwei Ebenen, bevor sie in den Baum bzw.
Export gehen. Antwort auf die Forderung "irgendeinen Verification Loop — technischen,
einen fachlichen". Angelehnt an Genealogical Proof Standard (GPS, BCG) + GEDCOM QUAY.

## Wann laden
- NACH jedem review_queue accept (data-capture schreibt in DB)
- VOR jedem genealogy-tree-archive Export (GEDCOM 7.0)
- AUF VERLANGEN: "pruef alles", "verification loop", "GPS-Check"

## TECHNISCHER LOOP (Maschinen-Integrität)
1. Referentielle Integrität:
   - Jede child_link.family_id existiert in family
   - Jede family.husband_id/wife_id existiert in person
   - person.id eindeutig (kein Dup)
2. DSGVO-Export-Leak: families.ged darf KEINE private=1 IDs enthalten
3. confidence-Constraint: alle Werte ∈ {belegt, unbestaetigt, Vermutung}
4. Quellen-Link-Erreichbarkeit: review_queue/pool_src URLs nicht tot (HTTP-Check stub)
5. OBJE-Pfade: verknüpfte Dateien existieren (sonst Warnung, nicht Fail)

## FACHLICHER LOOP (GPS-5 + QUAY)
Pro zu prüfende Person (Schwerpunkt: neu akzeptierte):
1. EXHAUSTIVE: wurden alle bekannten Quellen für Ort+Zeit abgecheckt?
   (source-research lookup_plan → fehlt eine? → Gap)
2. CITATION: hat jedes Fakt eine Quelle mit Signatur/URL?
   (person.notes/pool_src nicht leer; sonst "unzitiert")
3. CORRELATE: Interpretation plausibel? (kirchenbuch-deutung-Regeln beachtet)
4. CONTRADICTION: gibt es ZWEI Quellen mit widersprüchlichen Daten?
   → detection: gleiche person, unterschiedliche birth_date/death_date/eltern
   → output: review_queue "WIDERSPRUCH: @Ix@ Datum A vs B"
5. CONCLUSION: ist der Datensatz schlüssig dokumentiert (notes lesbar)?

QUAY-Bewertung (neu, als CHECK, nicht zwingend DB-Spalte):
- Primärquelle (Urkunde/KB-Scan) → QUAY 3 → confidence='belegt'
- OFB/Chronik → QUAY 2 → 'unbestaetigt'
- FS-Index/Web → QUAY 1 → 'unbestaetigt' (aber als "Index" markiert)
- Vermutung → QUAY 0 → 'Vermutung'
Hinweis: DB hat nur confidence-String. QUAY wird hier als Prüf-Logik geführt,
nicht als eigene Spalte (Erweiterung möglich, siehe Pitfalls).

## SCHRITT-FOLGE (Skript)
```python
import sqlite3
DB=r"D:\Ahnenforschung\db\working.sqlite"
c=sqlite3.connect(DB)
issues=[]
# technisch
for fid in c.execute("SELECT family_id FROM child_link"):
    if not c.execute("SELECT 1 FROM family WHERE id=?",fid).fetchone():
        issues.append(("TECH","child_link->family fehlt",fid[0]))
# fachlich: Widersprueche gleiche person mehrere Geburtsdaten?
# (person hat nur 1 birth_date; Widerspruch entsteht bei Merge/Dup -> dup-check)
dups=[r for r in c.execute("""SELECT given,surname,COUNT(*) FROM person 
       GROUP BY given,surname HAVING COUNT(*)>1""").fetchall()]
for d in dups: issues.append(("FACH","moegl. Dup (Widerspruch pruefen)",d))
# unzitiert
unc=[r[0] for r in c.execute("SELECT id FROM person WHERE notes IS NULL AND confidence='Vermutung'")]
for u in unc: issues.append(("FACH","Vermutung ohne Notiz/Quelle",u))
```
→ issues werden review_queue (status='pending', candidate='VERIFICATION: ...')

## VERIFIKATION (des Loops selbst)
- Loop liefert immer ein verification_report (Pass / Gaps+N)
- Bei 0 issues: "PASS — technisch+fachlich grün"
- Bei issues: review_queue-Einträge, Mensch entscheidet

## PITFALLS
- QUAY als DB-Spalte wäre sauberer (schema-Änderung nötig). Vorerst nur Prüf-Logik.
- "Exhaustive" ist schwer automatisierbar → nur als Gap-Hinweis (source-research),
  nicht als hartes Fail.
- Nicht mit name-research Integritätscheck verwechseln: das ist TECHNISCH (DB-Schema),
  dieser Skill ist TECHNISCH + FACHLICH (GPS).

## QUELLEN (GPS)
- Genealogical Proof Standard: https://www.familysearch.org/en/wiki/Genealogical_Proof_Standard
- BCG Standards: https://bcgcertification.org/ethics-standards/
- GEDCOM QUAY: https://gedcom.io/specs/55gctoc.html (Quality of Data)
