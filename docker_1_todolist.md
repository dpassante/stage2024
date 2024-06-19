### Exercice: Création d'une application de ToDo List avec Docker

**Objectif:** Cet exercice a pour but de vous familiariser avec Docker en créant une application simple de ToDo List. Vous allez apprendre à construire une image Docker, à exécuter un conteneur et à gérer les volumes pour la persistance des données.

**Prérequis:**
- Installation de Docker sur votre machine. Vous pouvez télécharger Docker Desktop depuis le site officiel: [Docker](https://www.docker.com/products/docker-desktop)

**Instructions détaillées:**

1. **Création de l'application ToDo List:**
   - Créez un nouveau dossier nommé `todo-app`.
   - À l'intérieur de ce dossier, créez un fichier `app.py` qui contiendra le code de votre application. Utilisez le framework Flask pour Python pour créer une application web simple.
   
   ```python
   from flask import Flask, request, render_template, redirect

   app = Flask(__name__)
   todos = []

   @app.route('/', methods=['GET', 'POST'])
   def todo():
       if request.method == 'POST':
           todo = request.form.get('todo')
           todos.append(todo)
       return render_template('index.html', todos=todos)

   if __name__ == '__main__':
       app.run(debug=True, host='0.0.0.0')
   ```

   - Créez un fichier `index.html` dans un dossier `templates` pour l'interface utilisateur de votre application.
   
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>ToDo List</title>
   </head>
   <body>
       <h1>ToDo List</h1>
       <form method="post">
           <input type="text" name="todo" placeholder="Add new task">
           <button type="submit">Add</button>
       </form>
       <ul>
           {% for todo in todos %}
           <li>{{ todo }}</li>
           {% endfor %}
       </ul>
   </body>
   </html>
   ```

2. **Création du fichier Dockerfile:**
   - À la racine du dossier `todo-app`, créez un fichier nommé `Dockerfile`.
   - Écrivez les instructions suivantes dans le Dockerfile pour créer l'image Docker de votre application.
   
   ```
   FROM python:3.8-slim
   WORKDIR /app
   COPY . /app
   RUN pip install flask
   EXPOSE 5000
   CMD ["python", "app.py"]
   ```

3. **Construction de l'image Docker:**
   - Ouvrez un terminal et naviguez jusqu'au dossier `todo-app`.
   - Exécutez la commande suivante pour construire l'image Docker de votre application:
     ```
     docker build -t todo-app .
     ```

4. **Exécution de l'application dans un conteneur Docker:**
   - Une fois l'image construite, exécutez l'application dans un conteneur Docker en utilisant la commande:
     ```
     docker run -p 5000:5000 todo-app
     ```
   - Ouvrez un navigateur et accédez à `http://localhost:5000` pour voir votre application ToDo List en action.

**Résultat attendu:**
- Vous devriez être capable de voir l'interface de votre ToDo List, d'ajouter des tâches et de voir la liste des tâches s'actualiser.

**Pour aller plus loin:**
- Essayez de modifier l'application pour permettre la suppression de tâches.
- Explorez la possibilité d'utiliser des volumes Docker pour la persistance des données de votre ToDo List.

Cet exercice vous permet de comprendre les bases de Docker et de voir comment une application simple peut être conteneurisée et exécutée localement. Bonne chance!
