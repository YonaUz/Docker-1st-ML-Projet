# Docker-1st-ML-Projet
Academic Project in Machine Learning with Docker 
# Projet 
Le projet vise à réaliser un conteneur Docker basé sur Docker Compose qui fait tourner un algorithme de Machine Learning. 
Voici l'arborescence du projet: 
/Hello_Flask: 
  - Dockerfile
  - run.py (port 8000)
  - /app :
      - __ init __ .py (sans espace mais ici c'est nécessaire sinon ça s'écrit en bold)
      - views.py
      - requirements.txt

/Recup: 
  - Dockerfile
  - run.py (port 7000)
  - /app :
    - __ init __ .py 
    - views.py 
    - requirements.txt

/Final:
  - Dockerfile
  - run.py (port 5000)
  - app:
    - __ init __ .py 
      - views.py
      - requirements.txt
compose.yml

# Préliminaires 
Afin d'initiliser le container Docker, il faut s'assurer de son fonctionnement et le lancer
** On le lance en mode interactif **
![3runnerlecontainer](https://user-images.githubusercontent.com/82390685/170138960-3f42a456-e39b-48a9-b9db-aff425e3395f.PNG)
** On le build **
![4build](https://user-images.githubusercontent.com/82390685/170139053-633f8e3a-34fc-4ea4-904b-d1a644935691.PNG)
** On constate le chargement des modules écrits dans le requirements.txt **
![5resultatdubuild](https://user-images.githubusercontent.com/82390685/170139143-7b82b4fa-2c6a-4485-8054-891e07ac76a7.PNG)
![7collectinfmodulesreponsesbuild](https://user-images.githubusercontent.com/82390685/170139186-5ff6bbdd-6689-4a1c-911e-635fd2e0238d.PNG)

# Principe 

J'ai décomposé le projet en 3 parties. 
Chaque container fonctionne sur le server Flask de Python qui permettra alors d'envoyer des données entre les fichiers. 

__Voici les fichiers run.py utilisés selon les ports appelés : __

![run py1](https://user-images.githubusercontent.com/82390685/170139285-5da4a065-03cc-4c32-8192-ad8674e0e0e0.PNG)

![run2](https://user-images.githubusercontent.com/82390685/170139369-cba4d310-1074-474c-b4d4-97eef50bde42.PNG)

![run3](https://user-images.githubusercontent.com/82390685/170139384-2709aa92-f855-45ef-8aba-07fafc842771.PNG)

__Voici les fichiers init.py utilisés (tous identiques)__

![init1](https://user-images.githubusercontent.com/82390685/170139502-d818f76d-5177-4b29-a3a4-f87f16811147.PNG)

__Voici le premier fichier views.py situé alors sur le port 8000:__

** Appel des librairies python **

![1](https://user-images.githubusercontent.com/82390685/170136669-5f969bd6-0ec4-4f6a-a86f-347b512efecd.PNG)

** On définit la régression linéaire **

![2](https://user-images.githubusercontent.com/82390685/170136849-bedc4b3f-5673-48df-849b-6cdbd251d6cd.PNG)

** On charge les données et on l'envoie sur l'adresse http://localhost:80000" **
** On définit l'échantillon de test et d'entrainement **

![3](https://user-images.githubusercontent.com/82390685/170136872-c40f9961-8529-4d72-8345-03614f27f68f.PNG)

__Voici ensuite le second fichier views.py qui charge ces données__

** On importe les modules comme précédemment et on récupère les données d'entrainement et de test du server précédent **
![4](https://user-images.githubusercontent.com/82390685/170137403-49237c9a-f469-4158-8d42-1cb7787caa6b.PNG)

** On calcule alors le modèle prédit par la régression linéaire et on l'envoie sur l'adresse http://localhost:7000" **
![5](https://user-images.githubusercontent.com/82390685/170137705-f4d201bf-fbbf-4d6d-a8df-92b8f1537c49.PNG)

__Voici le troisème fichier views.py qui charge le modèle prédit par ols et renvoie l'accuracy__

** On appelle le server précédent et on calcule l'accuracy **

![6](https://user-images.githubusercontent.com/82390685/170137972-9481e93b-394b-4db6-8657-ec4f5e935a74.PNG)

__Voici les fichier requirements.txt à implémenter dans les dossiers (ils sont identiques vus que les fichiers pythons appelés nécessitent les mêmes librairies__
![7](https://user-images.githubusercontent.com/82390685/170138385-98e1bce5-dcb2-470e-96c3-7b36600946f3.PNG)

__Voici le fichier compose.yml censé faire la connexion entre les différents dossiers et lancer ainsi le ML et donc lancer les servers__
![8](https://user-images.githubusercontent.com/82390685/170138572-a60069c9-f1e7-4811-8d10-a25b79cb037f.PNG)

__Voici un Dockerfile__
![9](https://user-images.githubusercontent.com/82390685/170138653-90f1be8c-2ebc-4e75-85b8-fc4deeb7a4e5.PNG)

__Mon résultat__ 
Mon projet ne fonctionne pas, je reste bloquée au tout début au téléchargement des modules:

![ERREURtelechargement](https://user-images.githubusercontent.com/82390685/170139625-19508888-5f84-43cb-b5d1-86b2252b5fdb.PNG)
