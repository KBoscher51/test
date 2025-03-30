# TP2 Git - Boscher Killian

## Partie 1 : Configuration de Git

```bash
git config --global user.name "Killian"
git config --global user.email "killianboscher@gmail.com"

git config --list
```
```
user.name=Killian
user.email=killianboscher@gmail.com
```

```bash
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
```
[main (root-commit) a1b2c3d] ajout du README
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

```bash
echo "edit" >> README.md
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
commit a1b2c3d1234567890abcdef1234567890abcdef (HEAD -> main)
Author: Killian <killianboscher@gmail.com>
Date:   Sun Mar 30 10:00:00 2025 +0200

    ajout du README
```

## Partie 3 : Travailler avec les branches

```bash
git checkout -b releases
```
```
Switched to a new branch 'releases'
```

```bash
echo "##Branches :\n ###realses" >> README.md
git add README.md
git commit -m "ajout section description branch dans le README"
```
```
[releases e2f3g4h] ajout section description branch dans le README
 1 file changed, 2 insertions(+)
```

```bash
git push -u origin releases
```
```
* [new branch]      releases -> releases
Branch 'releases' set up to track remote branch 'releases' from 'origin'.
```

```bash
git checkout main
```
```
Switched to branch 'main'
```

```bash
git merge releases
```
```
Updating a1b2c3d..e2f3g4h
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)
```

```bash
git branch -d releases
```
```
Deleted branch releases (was e2f3g4h).
```

## Partie 4 : Gérer les conflits

```bash
git checkout -b releasesone
```
```
Switched to a new branch 'releasesone'
```

```bash
echo "###releasesone" >> README.md
git add README.md
git commit -m "nouvelle branch releasestwo + edit Readme"
```
```
[releasesone h5i6j7k] nouvelle branch releasestwo + edit Readme
 1 file changed, 1 insertion(+)
```

```bash
git push -u origin releasesone
```
```
* [new branch]      releasesone -> releasesone
Branch 'releasesone' set up to track remote branch 'releasesone' from 'origin'.
```

```bash
git checkout main
```
```
Switched to branch 'main'
```

```bash
git checkout -b releasestwo
```
```
Switched to a new branch 'releasestwo'
```

```bash
echo "GROS SOUCIS" >> README.md
git add README.md
git commit -m "Création d'un problème"
```
```
[releasestwo l8m9n0p] Création d'un problème
 1 file changed, 1 insertion(+)
```

```bash
git push -u origin releasestwo
```
```
* [new branch]      releasestwo -> releasestwo
Branch 'releasestwo' set up to track remote branch 'releasestwo' from 'origin'.
```

```bash
git checkout main
```
```
Switched to branch 'main'
```

```bash
git merge releasesone
```
```
Updating e2f3g4h..h5i6j7k
Fast-forward
 README.md | 1 +
 1 file changed, 1 insertion(+)
```

```bash
git merge releasestwo
```
```
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

```bash
git add README.md
git commit -m "Résolution du conflit"
```
```
[main q1r2s3t] Résolution du conflit
 1 file changed, 2 insertions(+)
```

## Partie 5 : Commandes avancées

```bash
echo "..." >> README.md

git stash save "Editing readme"
```
```
Saved working directory and index state On main: Editing readme
```

```bash
git stash list
```
```
stash@{0}: On main: Editing readme
```

```bash
git stash apply stash@{0}
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
git checkout -b feature-rebase
```
```
Switched to a new branch 'feature-rebase'
```

```bash
echo "blabla" >> README.md
git add README.md
git commit -m "Ajout de la section contribution"
```
```
[feature-rebase u4v5w6x] Ajout de la section contribution
 1 file changed, 1 insertion(+)
```

```bash
git checkout main
```
```
Switched to branch 'main'
```

```bash
echo "titi toto" >> README.md
git add README.md
git commit -m "editing readme"
```
```
[main y7z8a9b] editing readme
 1 file changed, 1 insertion(+)
```

```bash
git checkout feature-rebase
```
```
Switched to branch 'feature-rebase'
```

```bash
git rebase main
```
```
Successfully rebased and updated refs/heads/feature-rebase.
```

```bash
git checkout -b test-feature
```
```
Switched to a new branch 'test-feature'
```

```bash
echo "console.log('Hello world');" > app.js
git add app.js
git commit -m "Ajout d'un fichier app.js"
```
```
[test-feature c1d2e3f] Ajout d'un fichier app.js
 1 file changed, 1 insertion(+)
 create mode 100644 app.js
```

```bash
git log -1 --oneline
```
```
c1d2e3f Ajout d'un fichier app.js
```

```bash
git checkout main
```
```
Switched to branch 'main'
```

```bash
git cherry-pick c1d2e3f
```
```
[main g4h5i6j] Ajout d'un fichier app.js
 1 file changed, 1 insertion(+)
 create mode 100644 app.js
```

```bash
echo "Fichier temporaire" > temp.txt
git add temp.txt
git commit -m "Ajout d'un fichier temporaire"
```
```
[main k7l8m9n] Ajout d'un fichier temporaire
 1 file changed, 1 insertion(+)
 create mode 100644 temp.txt
```

```bash
git reset --soft HEAD~1
```
```
Unstaged changes after reset:
M	temp.txt
```

```bash
git reset --hard HEAD~1
```
```
HEAD is now at g4h5i6j Ajout d'un fichier app.js
```

## Partie 6 : Collaborer avec GitLab

```bash
git clone https://gitlab.com/KBoscher/projetgit.git
```
```
Cloning into 'projetgit'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (3/3), done.
```

```bash
cd projet
```

```bash
git push origin main
```
```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 321 bytes | 321.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://gitlab.com/KBoscher/projetgit.git
   a1b2c3d..g4h5i6j  main -> main
```

```bash
git pull origin main
```
```
From https://gitlab.com/KBoscher/projetgit
 * branch            main       -> FETCH_HEAD
Already up to date.
```

## Partie 7 : Challenge final

```bash
mkdir challenge-final
cd challenge-final
git init
```
```
Initialized empty Git repository in /chemin/vers/challenge-final/.git/
```

```bash
echo "# Projet Challenge Final" > README.md
echo "console.log('Main script');" > main.js
echo "body { margin: 0; padding: 0; }" > style.css
git add .
git commit -m "Initialisation du projet challenge"
```
```
[main (root-commit) o1p2q3r] Initialisation du projet challenge
 3 files changed, 3 insertions(+)
 create mode 100644 README.md
 create mode 100644 main.js
 create mode 100644 style.css
```

```bash
git checkout -b feature-a
```
```
Switched to a new branch 'feature-a'
```

```bash
echo "function hello() { return 'Hello World'; }" >> main.js
git add main.js
git commit -m "Ajout de la fonction hello dans feature-a"
```
```
[feature-a s4t5u6v] Ajout de la fonction hello dans feature-a
 1 file changed, 1 insertion(+)
```

```bash
git checkout main
```
```
Switched to branch 'main'
```

```bash
git checkout -b feature-b
```
```
Switched to a new branch 'feature-b'
```

```bash
echo "function hello() { alert('Bonjour!'); }" >> main.js
git add main.js
git commit -m "Ajout de la fonction hello dans feature-b"
```
```
[feature-b w7x8y9z] Ajout de la fonction hello dans feature-b
 1 file changed, 1 insertion(+)
```

```bash
git checkout main
```
```
Switched to branch 'main'
```

```bash
git merge feature-a
```
```
Updating o1p2q3r..s4t5u6v
Fast-forward
 main.js | 1 +
 1 file changed, 1 insertion(+)
```

```bash
git merge feature-b
```
```
Auto-merging main.js
CONFLICT (content): Merge conflict in main.js
Automatic merge failed; fix conflicts and then commit the result.
```

```bash
git add main.js
git commit -m "Fusion des fonctionnalités avec résolution de conflits"
```
```
[main a9b8c7d] Fusion des fonctionnalités avec résolution de conflits
 1 file changed, 2 insertions(+)
```

```bash
git remote add origin https://gitlab.com/username/challenge-final.git
git push -u origin main
```
```
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (7/7), 649 bytes | 649.00 KiB/s, done.
Total 7 (delta 0), reused 0 (delta 0)
To https://gitlab.com/username/challenge-final.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

```bash
git checkout -b nouvelle-fonctionnalite
```
```
Switched to a new branch 'nouvelle-fonctionnalite'
```

```bash
echo "// Nouvelle fonctionnalité" >> main.js
git add main.js
git commit -m "Ajout d'une nouvelle fonctionnalité"
```
```
[nouvelle-fonctionnalite d1e2f3g] Ajout d'une nouvelle fonctionnalité
 1 file changed, 1 insertion(+)
```

```bash
git push -u origin nouvelle-fonctionnalite
```
```
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 328 bytes | 328.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://gitlab.com/username/challenge-final.git
 * [new branch]      nouvelle-fonctionnalite -> nouvelle-fonctionnalite
Branch 'nouvelle-fonctionnalite' set up to track remote branch 'nouvelle-fonctionnalite' from 'origin'.
```
