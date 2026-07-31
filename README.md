# DE-Ahnenforschung Skills

Deutschland-fokussierter Ahnenforschungs-Skill-Set für **Hermes Agent**.

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
