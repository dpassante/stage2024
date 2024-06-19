### Travaux Pratiques: Introduction à Python - Les Bases et les Fonctions

**Objectif:** Ce TP est conçu pour les débutants afin de les introduire aux commandes de base de Python et à la création de fonctions simples.

**Durée estimée:** 1 heure

**Prérequis:**
- Python installé sur votre machine. Vous pouvez le télécharger depuis le site officiel: [Python](https://www.python.org/downloads/)

**Instructions détaillées:**

1. **Découverte des types de données et des opérations de base:**
   - Créez un fichier `basics.py`.
   - Ouvrez ce fichier dans un éditeur de texte ou un IDE.
   - Écrivez des exemples de code pour démontrer les types de données de base: entiers, flottants, chaînes de caractères, listes, tuples et dictionnaires.
     ```python
     # Entiers et flottants
     a = 10
     b = 3.14

     # Chaînes de caractères
     name = "Alice"

     # Listes
     fruits = ["apple", "banana", "cherry"]

     # Tuples
     dimensions = (20, 30, 40)

     # Dictionnaires
     phone_book = {"John": "555-1234", "Jane": "555-5678"}
     ```

2. **Opérations de base:**
   - Ajoutez des exemples d'opérations arithmétiques, de concaténation de chaînes et d'accès aux éléments des listes et dictionnaires.
     ```python
     # Opérations arithmétiques
     sum = a + b
     product = a * b

     # Concaténation de chaînes
     greeting = "Hello, " + name + "!"

     # Accès aux éléments
     first_fruit = fruits[0]
     john_phone = phone_book["John"]
     ```

3. **Introduction aux fonctions:**
   - Créez des fonctions simples pour réutiliser le code.
     ```python
     def greet(person):
         return "Hello, " + person + "!"

     def add_numbers(x, y):
         return x + y

     def multiply_numbers(x, y):
         return x * y
     ```

4. **Utilisation des fonctions:**
   - Utilisez les fonctions que vous avez créées pour effectuer des opérations.
     ```python
     greeting = greet("Bob")
     sum = add_numbers(5, 3)
     product = multiply_numbers(4, 5)
     ```

5. **Exécution du script:**
   - Ouvrez un terminal ou une invite de commande.
   - Naviguez jusqu'au dossier contenant `basics.py`.
   - Exécutez le script en tapant `python basics.py`.
   - Ajoutez des `print` pour voir les résultats des opérations et des fonctions.
     ```python
     print(greeting)
     print("Sum:", sum)
     print("Product:", product)
     ```

**Résultat attendu:**
- Vous devriez être capable de comprendre et d'utiliser les types de données de base en Python, de réaliser des opérations simples et de créer et utiliser des fonctions.

**Pour aller plus loin:**
- Essayez de créer des fonctions plus complexes qui peuvent prendre des listes ou des dictionnaires comme paramètres et retourner des résultats basés sur ces structures.
- Explorez les boucles `for` et `while` pour manipuler et parcourir les listes et les dictionnaires.

Ce TP vous donne une introduction pratique aux bases de Python et vous prépare à explorer des concepts plus avancés en programmation. Bon apprentissage et amusez-vous bien avec Python!
