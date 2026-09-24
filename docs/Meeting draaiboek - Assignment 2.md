---
tags: [devops, source-control, meeting]
---

# Meeting draaiboek: Assignment 2 Source control

Zie ook: [[Assignment 2 - Source control - Plan van aanpak]], [[Voorbeeld commit messages]], [[pull_request_template]]

Temp repo: https://github.com/JeroenGilissenPXL/Temp-Team-Afspraken

## Voorbereiding (voor de meeting)

- [ ] Teams bericht met link naar de temp repo verstuurd
- [ ] Teamgenoten uitgenodigd als collaborator in de temp repo
- [ ] Github-gebruikersnamen van iedereen genoteerd
- [ ] Link naar de echte opdrachtrepo bij de hand
- [ ] Iedereen heeft toegang tot de echte opdrachtrepo
- [ ] Temp repo en deze notitie open in de browser en Obsidian

| Persoon | Naam   | Github-gebruikersnaam                                                         |                  |
| ------- | ------ | ----------------------------------------------------------------------------- | ---------------- |
| A       | Miet   | [**MietWelkenhuyzenPXL**](https://github.com/MietWelkenhuyzenPXL)             | Aftrekken        |
| B       | Felten | [**Pxl Felten Vanballenberghe**](https://github.com/FeltenVanballenberghePXL) | Vermenigvuldigen |
| C       | Jeroen | [**JeroenGilissenPXL**](https://github.com/JeroenGilissenPXL)                 | Delen            |

## 1. Opening (2 min)

- Doel van de meeting: afspraken maken zodat we de opdracht volgens de Github flow uit de cursus uitvoeren
- Aan het einde van de meeting staat de PR template op main van de opdrachtrepo en weet iedereen wat hij moet doen

## 2. Opdracht kort overlopen (3 min)

- Calculator heeft enkel add, wij voegen elk 1 feature toe
- Per feature: backend (`routes.js`), minstens 1 unittest, frontend (`index.html` en `frontend.js`)
- Mergen enkel via PR met akkoord van 2 personen
- Main is altijd deployable: nooit rechtstreeks op main committen

## 3. Verdeling van de features (5 min)

| Persoon | Feature | Branch |
|---|---|---|
| A | Aftrekken | `feature/subtract` |
| B | Vermenigvuldigen | `feature/multiply` |
| C | Delen | `feature/divide` |

Beslissing:
- A:Miet
- B:Felten
- C:Jeroen

## 4. Reviews en akkoord (3 min)

Github gratis laat maar 1 reviewer toe, de tweede persoon tagt je en geeft akkoord via een comment.

| PR van | Reviewer | Getagd voor akkoord |
|---|---|---|
| A | B | C |
| B | C | A |
| C | A | B |

Afspraak: geen lege "LGTM", maar inhoudelijke feedback.

## 5. Commit messages (5 min)

Scherm delen: [[Voorbeeld commit messages]]

- Regels van Chris Beams kort overlopen
- Klein en regelmatig committen
- Beslissen over de taal

Beslissing:
- Taal commit messages en PR's:  / Engels
- Branchnamen volgens `feature/<naam>`: ja 

## 6. PR template overlopen (5 min)

Scherm delen: `pull_request_template.md` in de temp repo

- Uitleggen: Github vult deze automatisch in bij elke nieuwe PR, zolang hij op main staat
- Samen overlopen: ontbreekt er iets, mag er iets weg?
- Afspraak: iedereen vult de template volledig in, de reviewer controleert dit mee

Aanpassingen:
-

## 7. Samen de PR voor de template maken (10 min)

Rollen:
- **Maker** (deelt scherm): ...
- **Reviewer**: ...
- **Tweede akkoord**: ...

### Stappen voor de maker

1. Echte opdrachtrepo openen op Github
2. **Add file** en daarna **Upload files**
3. `pull_request_template.md` (met de aanpassingen uit punt 6) in het venster slepen
4. Commit message: `Add pull request template`
5. Extra beschrijving: `Adds a PR template so every pull request has the same structure.`
6. Kiezen: **Create a new branch for this commit and start a pull request**
7. Branchnaam: `docs/pr-template`
8. **Propose changes**
9. PR titel: `Add pull request template`
10. Omschrijving invullen, reviewer toevoegen, tweede persoon taggen met `@naam`
11. **Create pull request**

### Stappen voor de reviewer

1. PR openen, tabblad **Files changed**
2. Minstens 1 inhoudelijke comment achterlaten
3. **Review changes**, **Approve**, **Submit review**

### Stappen voor het tweede akkoord

1. In de PR een comment plaatsen, bv. "Akkoord, template ziet er goed uit."

### Mergen

1. Maker klikt **Merge pull request** en **Confirm merge**
2. Controleren: staat `pull_request_template.md` nu op main?
3. Branch `docs/pr-template` voorlopig laten staan (zichtbaar voor de beoordeling)

## 8. Merge volgorde en merge conflicten (3 min)

- We wijzigen allemaal dezelfde bestanden, dus conflicten zijn bijna zeker
- PR's een voor een mergen
- Na elke merge: de anderen doen `git pull origin main` op hun eigen branch en lossen conflicten daar op

Afgesproken volgorde:
1.
2.
3.

## 9. Planning en afsluiting (4 min)

- [ ] Iedereen doet `git pull origin main` na de template-merge en start dan zijn feature branch
- [ ] Deadline eigen feature + PR open:
- [ ] Deadline reviews:
- [ ] Deadline alles gemerged:
- [ ] Volgende meeting of check-in:

## Actiepunten

| Wie | Wat | Tegen wanneer |
|---|---|---|
| | | |
| | | |
| | | |

## Notities

-
