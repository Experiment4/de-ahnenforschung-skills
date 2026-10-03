# DE-Ahnenforschung – Deutschlandspezifischer Skill‑Set für Hermes Agent

Herzlich willkommen beim **DE‑Ahnenforschung**‑Skill‑Set – dein persönlicher Assistent für die deutsche Genealogie, direkt im Hermes Agent.  
Egal, ob du gerade erst mit der Ahnenforschung beginnst oder bereits ein erfahrener Forscher bist: Dieses Set liefert dir alles, was du für eine strukturierte, quellensichere und DSGVO‑konforme Arbeit benötigst – alles auf Deutsch und passgenau auf die deutschen Quellen zugeschnitten.

## Warum dieses Skill‑Set?

* **Deutsch‑fokussiert** – Alle Skills sind speziell für die deutschen Archive, Kirchenbücher und Standesämter entwickelt.
* **Human‑in‑the‑Loop** – Der Agent sucht und vorschlägt, du entscheidest. So bleibt die Forschung kontrolliert und transparentsicher.
* **Modular aufgebaut** – Jeder Skill hat eine klare Ebene (0‑4) oder ist ein Querschnitts‑Skill, sodass du nur das laden musst, was du gerade brauchst.
* **Nahtlose Integration** – Das Set nutzt das gemeinsame `genealogy‑shared`‑Framework (SQLite‑Schema, `confidence`‑Konvention, `review_queue`‑Protokoll und Verzeichnislayout), damit alles harmonisch zusammenarbeitet.

## Was du bekommst

### Die neun Skills im Überblick

| Skill | Ebene | Was er für dich tut |
|-------|-------|--------------------|
| **de‑ahnenforschung‑roadmap** | Meta‑Router | Weist dir anhand deiner Aufgabe den richtigen Skill zu – kein Rätselraten mehr, welches Modul geladen werden soll. |
| **de‑ahnenforschung‑daten** | Ebene 1 | Nimmt deine Scans, Urkunden oder GEDCOM‑Dateien auf, normalisiert sie (Umlaute, historische Territorien, Windows‑Zeilenenden) und schreibt sie sicher in deine Arbeits‑SQLite. |
| **de‑ahnenforschung‑quellen** | Ebene 2 | Liefert dir die passende Quellen‑ und Sperrfristen‑Logic für jede Zeit und Region: Standesamt‑Sperrfristen (110/80/30 J), Matricula, Archion, CompGen, DFW und vieles mehr. |
| **de‑ahnenforschung‑kirchenbuecher** | Ebene 2 (Unter‑Skill) | Praktischer Zugang zu Matricula/Archion/FamilySearch: direkte Bild‑URLs, Download‑Skripte und Pfarreilisten‑Extraktion – damit du die Kirchenbücher bequem holen kannst. |
| **de‑ahnenforschung‑interpretation** | Ebene 0 | Dein Latein‑ und Kurrent/Sütterlin‑Glossar samt Hilfen zum Erkennen von Tauf‑, Heirats‑ und Sterbeeinträgen – ideal für alte Handschriften. |
| **de‑ahnenforschung‑verifikation** | Querschnitt | Prüft deine newly akzeptierten Personen sowohl technisch (Datenbank‑Integrität, DSGVO‑Leck) als auch fachlich (GPS‑5, QUAY‑Bewertung, Widerspruchs‑Erkennung) – bevor sie in den Baum oder Export gehen. |
| **de‑ahnenforschung‑export** | Ebene 3 | Exportiert deinen bestätigten Kern als GEDCOM 7.0 (Gramps‑kompatibel), versendet tägliche Review‑Reports an Discord/Telegram und legt DSGVO‑konforme Backups an. |
| **de‑ahnenforschung‑geschichte** | Kontext‑Skill | Vermittelt den historischen Rahmen: territoriale Entwicklungen von Preußen über die Weimarer Republik bis zur Bundesrepublik, Konfessionsgeschichte und Standesrecht – damit du deine Fakten richtig einordnen kannst. |
| **de‑ahnenforschung‑darstellung** | Ebene 4 | Zeichnet einen interaktiven Stammbaum direkt aus deiner SQLite‑DB (kein GEDCOM‑Export nötig), markiert unbelegte Fakten gelb und bietet Timeline, Geo‑Karte sowie Konfidenz‑Dashboard – alles auf Deutsch und sofort einsatzbereit. |

### Wie es zusammenarbeitet

1. **Roadmap** weist den passenden Skill zu.  
2. **Daten** bringen deine Rohmaterialien in die Datenbank.  
3. **Quellen** und **Kirchenbücher** zeigen dir, wo du suchen solltest und liefern die Bilder.  
4. **Interpretation** hilft beim Entziffern alter Schriften.  
5. **Agent‑Suche** (nicht im Set, aber über `genealogy‑agent‑search` verfügbar) liefert automatisch Kandidaten, die in die `review_queue` landen.  
6. **Verifikation** prüft jeden neuen Eintrag nach GPS‑5 und DSGVO.  
7. **Export** erzeugt schließlich dein finales GEDCOM und den Bericht.  
8. **Darstellung** lässt du deine Fortschritte live als Dashboard sehen.

## Installation

Das Skill‑Set lässt sich bequem über den Hermes SkillHub installieren:

```bash
hermes skills install --from de-ahnenforschung
```

### Manuelle Installation (falls du es lieber selbst kopierst)

```bash
# Repository klonen
git clone https://github.com/Experiment4/de-ahnenforschung-skills.git

# In dein Hermes‑Profil kopieren (Beispiel: profil "werkstatt")
cp -r de-ahnenforschung-skills/skills/de-ahnenforschung ~/.hermes/profiles/werkstatt/skills/

# Skills neu laden
hermes dev skills --reload
```

Nach der Installation stehen dir alle neun Skills sofort zur Verfügung – du kannst sie über die üblichen Hermes‑Befehle laden (`hermes skill load de-ahnenforschung-daten` usw.) oder sie über die Roadmap automatisch zuweisen lassen.

## Lizenz

Dieses Projekt steht unter der **MIT‑Lizenz** – siehe die Datei [LICENSE](LICENSE) für die vollständigen Bedingungen.

## Fragen & Feedback

Wenn du Anregungen hast, einen Bug gefunden hast oder einfach nur über deine neuesten Entdeckungen plaudern möchtest, öffne gerne ein Issue im Repository oder schreib uns direkt in den Hermes‑Discord. Wir freuen uns auf deine Rückmeldung und darauf, deine Forschung noch besser zu unterstützen.

Viel Erfolg beim Erkunden deiner Familiengeschichte – möge jeder neue Eintrag ein Stück lebendigerer Vergangenheit sein! 

---  
*Erstellt mit ❤️ von der Hermes‑Community und den Beitragenden von Experiment4/de-ahnenforschung-skills.*
