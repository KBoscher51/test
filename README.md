# TP2 Git - Boscher Killian

## Partie 1 : Configuration de Git

```bash
git config --global user.name "Killian"
git config --global user.email "killianboscher@gmail.com"

git config --list

mkdir projet-git
cd projet-git
git init
```

```
Initialized empty Git repository in /chemin/vers/projet-git/.git/
```

## Partie 2 : Les bases

```bash
echo "Mon tp2 git" > README.md

git add README.md

git commit -m "ajout du README"
```

```bash
echo "edit" >> README.md
git status
```

```bash
git log
```

## Partie 3 : Travailler avec les branches

```bash
git checkout -b releases
echo "##Branches :\n ###realses" >> README.md
git add README.md
git commit -m "ajout section description branch dans le README"
git push -u origin releases
```

```bash
git checkout main
git merge releases
```

```bash
git branch -d releases
```

## Partie 4 : Gérer les conflits

```bash
git checkout -b releasesone
echo "###releasesone" >> README.md
git add README.md
git commit -m "nouvelle branch releasestwo + edit Readme"
git push -u origin releasesone

git checkout main

git checkout -b releasestwo
echo "GROS SOUCIS" >> README.md
git add README.md
git commit -m "Création d'un problème"
git push -u origin releasestwo
```

```bash
git checkout main
git merge releasesone
git merge releasestwo
```

```bash
git add README.md
git commit -m "Résolution du conflit"
```

## Partie 5 : Commandes avancées

```bash
echo "..." >> README.md

git stash save "Editing readme"
```

```bash
git stash list
```

```bash
git stash apply stash@{0}
```

```bash
git checkout -b feature-rebase
echo "blabla" >> README.md
git add README.md
git commit -m "Ajout de la section contribution"

git checkout main
echo "titi toto" >> README.md
git add README.md
git commit -m "editing readme"

git checkout feature-rebase
git rebase main
```

```bash
git checkout -b test-feature
echo "console.log('Hello world');" > app.js
git add app.js
git commit -m "Ajout d'un fichier app.js"

git log -1 --oneline
```

```bash
git checkout main
git cherry-pick 1a2b3c4
```

```bash
echo "Fichier temporaire" > temp.txt
git add temp.txt
git commit -m "Ajout d'un fichier temporaire"

git reset --soft HEAD~1

git reset --hard HEAD~1
```

## Partie 6 : Collaborer avec GitLab

```bash
git clone https://gitlab.com/KBoscher/projetgit.git
cd projet

git push origin main

git pull origin main
```

## Partie 7 : Challenge final

```bash
mkdir challenge-final
cd challenge-final
git init
echo "# Projet Challenge Final" > README.md
echo "console.log('Main script');" > main.js
echo "body { margin: 0; padding: 0; }" > style.css
git add .
git commit -m "Initialisation du projet challenge"
```

```bash
git checkout -b feature-a
echo "function hello() { return 'Hello World'; }" >> main.js
git add main.js
git commit -m "Ajout de la fonction hello dans feature-a"

git checkout main
git checkout -b feature-b
echo "function hello() { alert('Bonjour!'); }" >> main.js
git add main.js
git commit -m "Ajout de la fonction hello dans feature-b"
```

```bash
git checkout main
git merge feature-a
git merge feature-b
git add main.js
git commit -m "Fusion des fonctionnalités avec résolution de conflits"
```

```bash
git remote add origin https://gitlab.com/username/challenge-final.git
git push -u origin main
```

```bash
git checkout -b nouvelle-fonctionnalite
echo "// Nouvelle fonctionnalité" >> main.js
git add main.js
git commit -m "Ajout d'une nouvelle fonctionnalité"
git push -u origin nouvelle-fonctionnalite
```
