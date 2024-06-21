### Travaux Pratiques: Déploiement d'une application Flask avec Redis en utilisant Docker

**Objectif:** Ce TP vise à vous familiariser avec Docker en déployant une application Flask simple qui utilise Redis comme base de données pour stocker des données. Vous apprendrez à gérer plusieurs conteneurs, à utiliser Docker Compose et à configurer une communication entre conteneurs.

**Durée estimée:** 1 heure

**Prérequis:**
- Docker et Docker Compose installés sur votre machine.
- Connaissances de base en Python et Flask.

**Instructions détaillées:**

1. **Préparation de l'environnement:**
   - Créez un nouveau dossier pour votre projet, par exemple `flask-redis-app`.
   - À l'intérieur de ce dossier, créez deux sous-dossiers: `app` pour le code source de l'application Flask et `redis` pour les fichiers de configuration de Redis (si nécessaire).

2. **Création de l'application Flask:**
   - Dans le dossier `app`, créez un fichier `app.py`:
     ```python
     from flask import Flask
     from redis import Redis

     app = Flask(__name__)
     redis = Redis(host='redis', port=6379)

     @app.route('/')
     def hello():
         count = redis.incr('hits')
         return 'Hello World! I have been seen {} times.\n'.format(count)

     if __name__ == "__main__":
         app.run(host="0.0.0.0", port=5000, debug=True)
     ```
   - Ajoutez un fichier `requirements.txt` pour les dépendances Python:
     ```
     flask
     redis
     ```

3. **Création du Dockerfile pour l'application Flask:**
   - Dans le dossier `app`, créez un fichier `Dockerfile`:
     ```
     FROM python:3.8-slim
     WORKDIR /code
     COPY ./app.py /code
     COPY ./requirements.txt /code
     RUN pip install -r requirements.txt
     CMD ["python", "app.py"]
     ```

4. **Utilisation de Docker Compose pour orchestrer les conteneurs:**
   - À la racine du projet (`flask-redis-app`), créez un fichier `docker-compose.yml`:
     ```yaml
     version: '3'
     services:
       web:
         build: ./app
         ports:
           - "5000:5000"
         depends_on:
           - redis
       redis:
         image: "redis:alpine"
     ```
   - Ce fichier configure deux services: `web` pour l'application Flask et `redis` pour le serveur Redis. `depends_on` assure que Redis est lancé avant l'application Flask.

5. **Construction et exécution des conteneurs:**
   - Ouvrez un terminal, naviguez jusqu'au dossier `flask-redis-app` et exécutez:
     ```
     docker-compose up --build
     ```
   - Attendez que Docker compose construise les images si nécessaire et démarre les conteneurs.

6. **Tester l'application:**
   - Ouvrez un navigateur et accédez à `http://localhost:5000`. Vous devriez voir un message indiquant combien de fois la page a été vue, ce nombre augmentant à chaque rechargement.

**Résultat attendu:**
- Vous avez une application Flask qui compte le nombre de visites et stocke ce compteur dans Redis. Chaque conteneur fonctionne ensemble grâce à Docker Compose.

**Pour aller plus loin:**
- Essayez d'ajouter une fonctionnalité à l'application, comme un formulaire pour insérer des données.
- Explorez les options de configuration de Redis pour la persistance des données.

Ce TP vous donne une bonne introduction à l'utilisation de Docker et Docker Compose pour déployer des applications multi-conteneurs. Vous avez maintenant une base solide pour explorer des déploiements plus complexes. Bon travail!
