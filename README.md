# Docker-1st-ML-Projet
Academic Project in Machine Learning with Docker 
# Projet 
Le projet vise à réaliser un conteneur Docker basé sur Docker Compose qui fait tourner un algorithme de Machine Learning. 
Voici l'arborescence du projet: 
/Hello_Flask: 
  - Dockerfile
  - run.py (port 8000)
  - /app :
      - __init__.py
      - views.py
      - requirements.txt

/Recup: 
  - Dockerfile
  - run.py (port 7000)
  - /app :
    - __init__.py
    - views.py 
    - requirements.txt

/Final:
  - Dockerfile
  - run.py (port 5000)
  - app:
    - __init__.py
      - views.py
      - requirements.txt
compose.yml

# Principe 
J'ai décomposé le projet en 3 parties. 
Chaque container fonctionne sur le server Flask de Python qui permettra alors d'envoyer des données entre les fichiers. 

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
