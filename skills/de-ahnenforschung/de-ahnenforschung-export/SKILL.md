---
name: de-ahnenforschung-export
description: "DE-Export: GEDCOM 7.0 Export, Review-Report, DSGVO-Ablage für Deutschland."
category: de-ahnenforschung
version: 1.0.0
author: Schrauberhirn
license: MIT
platforms: [windows]
---

# DE-Ahnenforschung — Export (EBENE 3)

## GEDCOM 7.0 Export

### Command
```bash
python scripts/export_gedcom_de.py --db D:\Ahnenforschung\db\working.sqlite
```

### Output
- Datei: `D:\Ahnenforschung\gedcom\families_de.ged`
- Gramps/Ancestry/FamilySearch kompatibel
- DE-Charakterkodierung: UTF-8 mit Umlauten

## Review-Report

### Daily Report
- Wird an Discord/Telegram gesendet
- Inhalt: neue akzeptierte Personen, ungeprüfte Fakten, Quellen-Lücken

### Command
```bash
python scripts/review_report_de.py --db D:\Ahnenforschung\db\working.sqlite --channel discord
```

## DSGVO-konforme Ablage

### Regeln
- Lebende Personen: geschützt, keine Cloud-Uploads
- Token/Secrets: `D:\Ahnenforschung\fs_token.txt`, nie loggen
- Backup: `D:\backups`, verschlüsselt

## Related
[[de-ahnenforschung-roadmap]]
[[de-ahnenforschung-darstellung]]