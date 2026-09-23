---
tags: [devops, source-control, github-flow, opdracht]
---

# Assignment 2: Source control - Plan van aanpak

Zie ook: [[pull_request_template]] en [[Voorbeeld commit messages]]

## De opdracht in het kort

- Calculator applicatie (NodeJS) heeft enkel een add functie
- Elk teamlid bouwt 1 nieuwe feature volgens de **Github flow**
- Per feature: backend (`routes.js`), minstens 1 unittest, frontend (`public/index.html` en `public/frontend.js`)
- Mergen naar main enkel via een **pull request** met toestemming van **2 personen**
- Werken op de Linux VM uit les 1

### Commando's

```bash
npm install   # dependencies installeren
npm start     # app starten op http://localhost:3000
npm test      # unittesten uitvoeren
```

## Verdeling (3 personen)

| Persoon | Feature | Branch | Reviewer | Getagd in PR |
|---|---|---|---|---|
| A | Aftrekken | `feature/subtract` | B | C |
| B | Vermenigvuldigen | `feature/multiply` | C | A |
| C | Delen | `feature/divide` | A | B |

- Github gratis laat maar 1 reviewer toe: de andere persoon tag je in de PR en die geeft akkoord via een comment
- Door te rouleren reviewt iedereen 1 keer en geeft iedereen 1 keer akkoord

## Github flow (volgens de slides)

1. Developer maakt een feature in een aparte branch in zijn lokale repo
2. Developer pusht de branch naar de centrale repository op Github
3. Developer start een pull request via Github
4. De rest van het team evalueert de code, geeft feedback, er wordt aangepast
5. De verantwoordelijke merget de wijzigingen naar main en sluit de PR

### Stappen per persoon

```bash
git checkout main
git pull origin main
git checkout -b feature/subtract

# werken + regelmatig committen
git add routes.js
git commit            # opent editor voor multi line commit message

# regelmatig pushen
git push origin feature/subtract
```

Daarna op Github: pull request openen van `feature/subtract` naar `main`.

## Aandachtspunten

### 1. Main is altijd deployable
- Nooit rechtstreeks op main committen
- Altijd `npm test` draaien voor je een PR opent
- Mergen via een pull request, niet via een lokale `git merge`

### 2. Goede commit messages (Chris Beams)
- Onderwerpregel kort, max. ongeveer 50 tekens
- Beginnen met een hoofdletter, geen punt op het einde
- Gebiedende wijs: "Add subtract route", niet "Added" of "Adding"
- Lege regel tussen onderwerp en body
- Body max. ongeveer 72 tekens per regel
- In de body uitleggen **wat** en **waarom**, niet **hoe**
- Klein en regelmatig committen, in logische stappen

### 3. Goede pull requests
- Duidelijke titel en omschrijving
- Teamgenoten taggen (`@naam`)
- 1 reviewer toevoegen
- `pull_request_template.md` in de root van de repo zetten (zie [[pull_request_template]])

### 4. Echte review
- Geen lege "LGTM", maar inhoudelijke feedback
- Liefst minstens 1 opmerking die leidt tot een extra commit in de PR (toont stap 4 van de flow)
- Tweede persoon geeft expliciet akkoord via een comment

### 5. Merge conflicten
Iedereen wijzigt dezelfde bestanden, dus conflicten zijn bijna zeker.

1. PR's **een voor een** mergen, niet tegelijk
2. Na elke merge halen de anderen de nieuwe main binnen in hun eigen branch:
   ```bash
   git checkout feature/multiply
   git pull origin main
   # conflicten oplossen in de bestanden
   git add .
   git commit
   git push origin feature/multiply
   ```
3. De PR is daarna weer mergebaar

## Checklist per feature

- [ ] Feature branch aangemaakt met duidelijke naam
- [ ] Backend in `routes.js`
- [ ] Minstens 1 unittest (bij delen ook een test voor delen door nul)
- [ ] Frontend in `public/index.html` en `public/frontend.js`
- [ ] `npm test` slaagt
- [ ] Meerdere kleine commits met goede messages
- [ ] Branch gepusht naar Github
- [ ] PR met omschrijving volgens template
- [ ] Reviewer toegevoegd, andere teamgenoot getagd
- [ ] Inhoudelijke review en 2 keer akkoord
- [ ] Gemerged naar main via de PR

## Deliverable (moet zichtbaar zijn op Github)

- [ ] Aparte feature branch per feature
- [ ] Een PR per feature branch
- [ ] Elke feature: backend, frontend en unittesten
- [ ] Main branch met de laatste versie van de code
- [ ] Goede en gestructureerde commit messages en PR messages
- [ ] Duidelijke review in de PR's

> Let op: de slides tonen `git branch -d` na een merge. Verwijder de feature branches pas na de beoordeling, of controleer dat ze nog zichtbaar zijn via de PR.
