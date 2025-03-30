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
echo "# Mon Projet Git\nCe projet est réalisé dans le cadre du TP Git." > README.md

git add README.md

git commit -m "Premier commit : ajout du README"
```

```
[main (root-commit) f7d2e3a] Premier commit : ajout du README
 1 file changed, 2 insertions(+)
 create mode 100644 README.md
```

```bash
echo "\nAjout d'une nouvelle ligne pour tester les modifications." >> README.md
git status
```

```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

```bash
git log
```

```
commit f7d2e3a1234567890abcdef1234567890abcdef (HEAD -> main)
Author: Killian Boscher <killian.boscher@example.com>
Date:   Sun Mar 30 10:00:00 2025 +0200

    Premier commit : ajout du README
```

## Partie 3 : Travailler avec les branches

```bash
git branch feature-description

git checkout feature-description
echo "\n## Description\nCe projet permet d'explorer les commandes Git." >> README.md
git add README.md
git commit -m "Ajout d'une section description dans le README"
```

```
[feature-description 3c4d5e6] Ajout d'une section description dans le README
 1 file changed, 2 insertions(+)
```

```bash
git checkout main
git merge feature-description
```

```
Updating f7d2e3a..3c4d5e6
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)
```

```bash
git branch -d feature-description
```

```
Deleted branch feature-description (was 3c4d5e6).
```

## Partie 4 : Gérer les conflits

```bash
git checkout -b section-installation
echo "\n## Installation\nClonez ce dépôt et lancez l'application." >> README.md
git add README.md
git commit -m "Ajout de la section installation"

git checkout main

git checkout -b section-config
echo "\n## Installation\nTéléchargez le ZIP et suivez les étapes du guide." >> README.md
git add README.md
git commit -m "Ajout d'une autre version de la section installation"
```

```bash
git checkout main
git merge section-installation
git merge section-config
```

```
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

```bash
git add README.md
git commit -m "Résolution du conflit dans la section installation"
```

```
[main 7g8h9i0] Résolution du conflit dans la section installation
```

## Partie 5 : Commandes avancées

```bash
echo "\n## Fonctionnalités\n- Gestion des utilisateurs\n- Configuration avancée" >> README.md

git stash save "Ajout de la section fonctionnalités"
```

```
Saved working directory and index state On main: Ajout de la section fonctionnalités
```

```bash
git stash list
```

```
stash@{0}: On main: Ajout de la section fonctionnalités
```

```bash
git stash apply stash@{0}
```

```bash
git checkout -b feature-rebase
echo "\n## Contribution\nLes contributions sont les bienvenues." >> README.md
git add README.md
git commit -m "Ajout de la section contribution"

git checkout main
echo "\n## Licence\nMIT" >> README.md
git add README.md
git commit -m "Ajout de la section licence"

git checkout feature-rebase
git rebase main
```

```
Successfully rebased and updated refs/heads/feature-rebase.
```

```bash
git checkout -b test-feature
echo "console.log('Hello world');" > app.js
git add app.js
git commit -m "Ajout d'un fichier app.js"

git log -1 --oneline
```

```
1a2b3c4 Ajout d'un fichier app.js
```

```bash
git checkout main
git cherry-pick 1a2b3c4
```

```
[main 5d6e7f8] Ajout d'un fichier app.js
 Date: Sun Mar 30 11:30:00 2025 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 app.js
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
git clone https://gitlab.com/username/projet.git
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
