---
tags: [devops, source-control, linux, git, ssh]
---

# Linux setup: Git, SSH sleutel en clone

Zie ook: [[Assignment 2 - Source control - Plan van aanpak]]

Alles hieronder voer je uit in de terminal van je **Linux VM uit les 1**. Dit doe je eenmalig per VM.

## 1. Controleren wat er al staat

```bash
git --version
node --version
npm --version
```

Ontbreekt er iets (Ubuntu of Debian):

```bash
sudo apt update
sudo apt install git nodejs npm
```

## 2. Git configureren

Git zet je naam en e-mail bij elke commit. Gebruik hetzelfde e-mailadres als op je Github-account, anders worden je commits niet aan jou gekoppeld.

```bash
git config --global user.name "Voornaam Achternaam"
git config --global user.email "jouw@email.be"
git config --global init.defaultBranch main
git config --global core.editor nano
```

Controleren:

```bash
git config --list
```

## 3. SSH sleutel aanmaken

Met een SSH sleutel kan je pushen en pullen zonder telkens een wachtwoord of token in te geven. Github aanvaardt geen gewoon wachtwoord meer via HTTPS.

Eerst kijken of je al een sleutel hebt:

```bash
ls ~/.ssh
```

Zie je `id_ed25519` en `id_ed25519.pub`, dan kan je naar stap 4. Anders maak je er een aan:

```bash
ssh-keygen -t ed25519 -C "jouw@email.be"
```

- Vraag naar de locatie: gewoon **Enter** (standaard `~/.ssh/id_ed25519`)
- Vraag naar een passphrase: kies er een, of druk twee keer **Enter** voor geen passphrase

Je krijgt twee bestanden:

| Bestand | Wat | Delen? |
|---|---|---|
| `~/.ssh/id_ed25519` | Private sleutel | **Nooit** delen of uploaden |
| `~/.ssh/id_ed25519.pub` | Publieke sleutel | Deze zet je op Github |

## 4. Sleutel toevoegen aan de ssh-agent

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

Heb je een passphrase gekozen, dan vraagt hij die hier een keer.

## 5. Publieke sleutel op Github zetten

Publieke sleutel tonen:

```bash
cat ~/.ssh/id_ed25519.pub
```

Kopieer de volledige regel (begint met `ssh-ed25519` en eindigt met je e-mail).

Op Github:
1. Rechtsboven op je profielfoto, dan **Settings**
2. Links **SSH and GPG keys**
3. **New SSH key**
4. Title: bv. `Linux VM PXL`
5. Key type: **Authentication Key**
6. Plak de sleutel en klik **Add SSH key**

## 6. Verbinding testen

```bash
ssh -T git@github.com
```

- De eerste keer vraagt hij of je de host vertrouwt: typ `yes`
- Gelukt als je ziet: `Hi <gebruikersnaam>! You've successfully authenticated...`

## 7. De opdrachtrepo clonen

Op Github in de repo: groene knop **Code**, tabblad **SSH**, link kopieren. Die begint met `git@github.com:`.

```bash
mkdir -p ~/git
cd ~/git
git clone git@github.com:<account>/<repo-naam>.git
cd <repo-naam>
```

Controleren:

```bash
git remote -v      # moet git@github.com:... tonen
git branch         # je staat op main
git log --oneline  # bestaande commits
```

## 8. App klaarzetten en testen

```bash
npm install
npm test
npm start
```

Surf in de browser van de VM naar http://localhost:3000. Stoppen met **Ctrl+C**.

## 9. Klaar om te starten

Pas als de PR template op main staat (zie [[Meeting draaiboek - Assignment 2]]):

```bash
git checkout main
git pull origin main
git checkout -b feature/<jouw-feature>
```

## Problemen

**`Permission denied (publickey)`**
De sleutel staat niet op Github of niet in de ssh-agent. Stap 4 en 5 opnieuw doen en testen met `ssh -T git@github.com`.

**Repo al gecloned via HTTPS en pushen vraagt een wachtwoord**
Remote omzetten naar SSH:
```bash
git remote set-url origin git@github.com:<account>/<repo-naam>.git
```

**`Repository not found`**
Je hebt geen toegang. Vraag de eigenaar je toe te voegen als collaborator en aanvaard de uitnodiging (via e-mail of github.com/notifications).

**Commits staan niet op mijn naam op Github**
Het e-mailadres in `git config user.email` komt niet overeen met je Github-account. Aanpassen voor de volgende commits.

**`npm: command not found`**
NodeJS is niet geinstalleerd, zie stap 1.

## Checklist

- [ ] Git, NodeJS en npm geinstalleerd
- [ ] `user.name` en `user.email` ingesteld
- [ ] SSH sleutel aangemaakt
- [ ] Publieke sleutel op Github gezet
- [ ] `ssh -T git@github.com` gelukt
- [ ] Opdrachtrepo gecloned via SSH
- [ ] `npm install` en `npm test` gelukt
- [ ] App draait op http://localhost:3000
