### Travaux Pratiques: Déploiement d'une Application LAMP sur Docker

**Objectif:** Ce TP vise à vous familiariser avec Docker en déployant une application LAMP (Linux, Apache, MySQL, PHP) sur deux conteneurs Docker distincts : un pour la base de données MySQL et un autre pour le serveur web Apache avec PHP.

**Durée estimée:** 1 heure

**Prérequis:**
- Docker et Docker Compose installés sur votre machine.
- Connaissances de base en manipulation de Docker et en développement web.

**Instructions détaillées:**

1. **Préparation de l'environnement:**
   - Créez un nouveau dossier pour votre projet, par exemple `lamp-app`.
   - À l'intérieur de ce dossier, créez deux sous-dossiers: `db` pour les fichiers de configuration de la base de données et `web` pour les fichiers du serveur web.

2. **Configuration de la base de données MySQL:**
   - Dans le dossier `db`, créez un fichier `init.sql` qui contiendra les instructions SQL pour créer une base de données et une table de test.
     ```sql
     CREATE DATABASE IF NOT EXISTS example_db;
     USE example_db;
     CREATE TABLE IF NOT EXISTS users (
       id INT AUTO_INCREMENT PRIMARY KEY,
       username VARCHAR(255) NOT NULL
     );
     INSERT INTO users (username) VALUES ('Alice'), ('Bob');
     ```

3. **Création de l'application web PHP:**
   - Dans le dossier `web`, créez un fichier `index.php`:
     ```php
     <?php
     $conn = new mysqli("db", "root", "example", "example_db");
     if ($conn->connect_error) {
         die("Connection failed: " . $conn->connect_error);
     }
     $result = $conn->query("SELECT username FROM users");
     echo "<ul>";
     while ($row = $result->fetch_assoc()) {
         echo "<li>" . $row["username"] . "</li>";
     }
     echo "</ul>";
     $conn->close();
     ?>
     ```

4. **Création du Dockerfile pour Apache et PHP:**
   - Dans le dossier `web`, créez un fichier `Dockerfile`:
     ```
     FROM php:7.4-apache
     COPY . /var/www/html/
     ```

5. **Utilisation de Docker Compose pour orchestrer les conteneurs:**
   - À la racine du projet (`lamp-app`), créez un fichier `docker-compose.yml`:
     ```yaml
     version: '3'
     services:
       db:
         image: mysql:5.7
         volumes:
           - ./db/init.sql:/docker-entrypoint-initdb.d/init.sql
         environment:
           MYSQL_ROOT_PASSWORD: example
       web:
         build: ./web
         ports:
           - "8000:80"
         depends_on:
           - db
     ```
   - Ce fichier configure deux services: `db` pour MySQL et `web` pour Apache/PHP. `depends_on` assure que MySQL est lancé avant Apache/PHP.

6. **Construction et exécution des conteneurs:**
   - Ouvrez un terminal, naviguez jusqu'au dossier `lamp-app` et exécutez:
     ```
     docker-compose up --build
     ```
   - Attendez que Docker Compose construise les images si nécessaire et démarre les conteneurs.

7. **Tester l'application:**
   - Ouvrez un navigateur et accédez à `http://localhost:8000`. Vous devriez voir une liste des utilisateurs récupérés de la base de données MySQL.

**Résultat attendu:**
- Vous avez une application LAMP fonctionnelle avec une base de données MySQL et un serveur web Apache/PHP, le tout déployé sur Docker.

**Pour aller plus loin:**
- Essayez d'ajouter plus de fonctionnalités à l'application PHP, comme des formulaires pour ajouter ou supprimer des utilisateurs.
- Explorez la sécurisation de la connexion à la base de données et la gestion des erreurs en PHP.

Ce TP vous donne une bonne introduction à l'utilisation de Docker pour déployer une application LAMP. Vous avez maintenant une base solide pour explorer des déploiements plus complexes. Bonne chance!
