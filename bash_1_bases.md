### Travaux Pratiques: Introduction à Bash - Commandes de Base et Scripts Simples

**Objectif:** Ce TP est conçu pour initier les débutants aux commandes de base de Bash et à la création de scripts simples.

**Durée estimée:** 1 heure

**Prérequis:**
- Avoir accès à un terminal Linux ou utiliser Git Bash sous Windows.

**Instructions détaillées:**

1. **Découverte des commandes de base:**
   - Ouvrez votre terminal.
   - Tapez `pwd` pour afficher le répertoire de travail actuel.
   - Utilisez `ls` pour lister les fichiers et dossiers dans le répertoire actuel.
   - Changez de répertoire avec `cd nom_dossier`.
   - Créez un nouveau dossier avec `mkdir mon_dossier`.
   - Naviguez dans ce dossier avec `cd mon_dossier`.

2. **Manipulation de fichiers:**
   - Créez un nouveau fichier avec `touch mon_fichier.txt`.
   - Ouvrez ce fichier avec un éditeur en ligne de commande, par exemple `nano mon_fichier.txt`.
   - Écrivez quelques lignes de texte, sauvegardez et quittez l'éditeur.
   - Affichez le contenu du fichier avec `cat mon_fichier.txt`.
   - Copiez le fichier avec `cp mon_fichier.txt copie.txt`.
   - Renommez le fichier copié avec `mv copie.txt nouveau_nom.txt`.
   - Supprimez le fichier renommé avec `rm nouveau_nom.txt`.

3. **Introduction aux scripts Bash:**
   - Créez un nouveau script avec `nano mon_script.sh`.
   - Écrivez un script simple pour afficher "Hello, World!" et la date et l'heure actuelles:
     ```bash
     #!/bin/bash
     echo "Hello, World!"
     echo "Il est actuellement $(date)"
     ```
   - Rendez le script exécutable avec `chmod +x mon_script.sh`.
   - Exécutez le script avec `./mon_script.sh`.

4. **Utilisation des variables et des boucles:**
   - Modifiez `mon_script.sh` pour utiliser une variable et une boucle:
     ```bash
     #!/bin/bash
     greeting="Bonjour"
     for name in Alice Bob Charlie
     do
       echo "$greeting, $name!"
     done
     ```
   - Sauvegardez et exécutez le script modifié.

5. **Exécution du script:**
   - Assurez-vous que le script est toujours exécutable.
   - Exécutez le script modifié pour voir les salutations personnalisées.

**Résultat attendu:**
- Vous devriez être capable de comprendre et d'utiliser les commandes de base de Bash, de manipuler des fichiers et des dossiers, et de créer et exécuter des scripts simples.

**Pour aller plus loin:**
- Essayez d'ajouter des conditions avec `if...else` dans vos scripts.
- Explorez comment lire l'entrée de l'utilisateur avec la commande `read`.
- Apprenez à rediriger les sorties des commandes dans des fichiers ou d'autres commandes avec `>`, `>>` et `|`.

Ce TP vous offre une introduction pratique à Bash, vous préparant à explorer des scripts plus complexes et à automatiser des tâches sous Linux. Bon apprentissage et amusez-vous bien avec Bash!
