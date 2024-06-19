### Travaux Pratiques: Maîtriser les Commandes de Base du Shell Linux

**Objectif:** Ce TP vise à vous familiariser avec les commandes de base du shell Linux, vous permettant de naviguer dans le système de fichiers, de gérer les fichiers et d'utiliser des commandes de filtrage et de redirection.

**Durée estimée:** 1 heure

**Prérequis:**
- Accès à un terminal Linux.

**Instructions détaillées:**

1. **Navigation dans le système de fichiers:**
   - Ouvrez votre terminal.
   - Utilisez `pwd` pour afficher le chemin du répertoire courant.
   - Tapez `ls` pour lister les fichiers et dossiers dans le répertoire courant.
   - Changez de répertoire avec `cd /chemin/vers/dossier` et revenez avec `cd ..`.
   - Créez un nouveau dossier avec `mkdir mon_nouveau_dossier` et naviguez dedans.

2. **Gestion des fichiers:**
   - Dans le nouveau dossier, créez un fichier vide nommé `test.txt` avec `touch test.txt`.
   - Écrivez "Bonjour le monde" dans ce fichier en utilisant `echo "Bonjour le monde" > test.txt`.
   - Affichez le contenu du fichier avec `cat test.txt`.
   - Copiez le fichier avec `cp test.txt copie.txt`.
   - Renommez le fichier copié avec `mv copie.txt nouveau_nom.txt`.
   - Supprimez le fichier renommé avec `rm nouveau_nom.txt`.

3. **Utilisation des commandes de filtrage:**
   - Créez un nouveau fichier `liste.txt` et ajoutez-y plusieurs lignes de texte.
   - Utilisez `grep "motif" liste.txt` pour rechercher des lignes contenant un motif spécifique.
   - Affichez les premières lignes d'un fichier avec `head -n 5 liste.txt`.
   - Affichez les dernières lignes d'un fichier avec `tail -n 5 liste.txt`.
   - Triez le contenu d'un fichier avec `sort liste.txt`.

4. **Redirection et chaînage de commandes:**
   - Redirigez la sortie d'une commande vers un fichier avec `commande > fichier`.
   - Ajoutez la sortie à la fin d'un fichier existant avec `commande >> fichier`.
   - Utilisez le pipe `|` pour utiliser la sortie d'une commande comme entrée d'une autre, par exemple `cat liste.txt | grep "motif"`.

5. **Scripts de base en Bash:**
   - Créez un script `script.sh` avec `nano script.sh`.
   - Écrivez un script simple qui affiche la date et l'heure actuelles, le contenu du répertoire courant et le contenu d'un fichier spécifié:
     ```bash
     #!/bin/bash
     echo "Date et heure actuelles:"
     date
     echo "Contenu du répertoire courant:"
     ls
     echo "Contenu du fichier spécifié:"
     cat $1
     ```
   - Rendez le script exécutable avec `chmod +x script.sh`.
   - Exécutez le script en passant `test.txt` comme argument avec `./script.sh test.txt`.

**Résultat attendu:**
- Vous devriez être capable de naviguer efficacement dans le système de fichiers, de gérer des fichiers, d'utiliser des commandes de filtrage et de redirection, et d'écrire des scripts de base en Bash.

**Pour aller plus loin:**
- Explorez les commandes avancées comme `find`, `awk`, et `sed`.
- Apprenez à gérer les processus avec `ps`, `top`, `kill`, etc.
- Pratiquez la création de scripts Bash plus complexes qui utilisent des boucles, des conditions, et des fonctions.

Ce TP vous offre une introduction pratique aux commandes de base du shell Linux, vous préparant à explorer des utilisations plus avancées et à automatiser des tâches sous Linux. Bon apprentissage et amusez-vous bien avec le shell Linux!
