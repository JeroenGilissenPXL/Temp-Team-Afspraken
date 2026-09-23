---
tags: [devops, source-control, commit-messages]
---

# Voorbeeld commit messages

Zie ook: [[Assignment 2 - Source control - Plan van aanpak]]

## De 7 regels (Chris Beams)

1. Onderwerp en body scheiden met een lege regel
2. Onderwerpregel max. ongeveer 50 tekens
3. Onderwerpregel begint met een hoofdletter
4. Geen punt op het einde van de onderwerpregel
5. Gebiedende wijs in de onderwerpregel ("Add", "Fix", "Update")
6. Body max. ongeveer 72 tekens per regel
7. Body legt uit **wat** en **waarom**, niet **hoe**

Handige test: de onderwerpregel moet deze zin logisch afmaken:
*"If applied, this commit will ..."*

## Multi line commit maken

```bash
git commit
```

Zonder `-m` opent git een editor waarin je onderwerp, lege regel en body kan schrijven.

Alternatief met meerdere `-m` flags (elke `-m` wordt een aparte alinea):

```bash
git commit -m "Add subtract route to backend" -m "Customers asked for a way to subtract two numbers."
```

## Goed vs slecht

| Slecht | Goed |
|---|---|
| `fixed stuff` | `Fix wrong result when subtracting negatives` |
| `Added the subtract function.` | `Add subtract route to backend` |
| `update` | `Update frontend with multiply button` |
| `wip` | `Add unit test for divide by zero` |
| `changes to routes.js, index.html and frontend.js and tests` | Opsplitsen in meerdere commits |

## Persoon A: aftrekken (`feature/subtract`)

```
Add subtract route to backend

Customers asked for a subtract function in the calculator. This adds
a /subtract route in routes.js that returns the difference of two
numbers.
```

```
Add unit test for subtract route

Verifies that the subtract route returns the correct difference,
including results below zero.
```

```
Add subtract button to frontend

Adds a subtract button to index.html and connects it to the new
backend route in frontend.js.
```

## Persoon B: vermenigvuldigen (`feature/multiply`)

```
Add multiply route to backend

Adds a /multiply route in routes.js so the calculator can return the
product of two numbers.
```

```
Add unit tests for multiply route

Covers regular multiplication and multiplication by zero.
```

```
Add multiply button to frontend
```

## Persoon C: delen (`feature/divide`)

```
Add divide route to backend

Adds a /divide route in routes.js that returns the quotient of two
numbers.
```

```
Handle division by zero in divide route

Dividing by zero returned Infinity, which is not a useful result for
users. The route now returns an error message instead.
```

```
Add unit tests for divide route

Tests a regular division and the division by zero case.
```

```
Add divide button to frontend
```

## Na review of merge conflict

```
Rename subtract variables for readability

Addresses review feedback from @persoonB: variable names a and b were
unclear, renamed to minuend and subtrahend.
```

```
Resolve merge conflict with main in routes.js

Main now contains the subtract route. Kept both the subtract and the
multiply routes.
```

## Voorbeeld PR titel en omschrijving

**Titel:** `Add subtract function to calculator`

**Omschrijving:**
Deze PR voegt een aftrek functie toe aan de calculator, op vraag van klanten.

- Backend: nieuwe `/subtract` route in `routes.js`
- Frontend: knop in `index.html`, afhandeling in `frontend.js`
- Tests: unittest voor de subtract route

`npm test` slaagt lokaal en manueel getest via localhost:3000.

Reviewer: @persoonB
Akkoord gevraagd aan: @persoonC
