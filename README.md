# Docker

## Objectif

 Faire communiquer un container de serveur web __tomcat:8-jre8__ avec un container de base de donnée __postgres:9.5__.
 
 #### IMPORTANT : Le container de la base de donnée doit être crée avant le container du serveur web

 ### Etape 1 : Création du container de base de donnée
 
1) Se placer dans le dossier __postgres__

2) Créer l'image à partir du Dockerfile 

        docker build -t <name image bdd> .
        
3) Créer le container à partir de l'image <name image>
  
        docker run -d --name <name container bdd> -v /var/lib/postgresql/data /<name image>
 
### Etape 2 : Création du container de serveur web

1) Se placer dans le dossier __tomcat__

2) Créer l'image à partir du Dockerfile

        docker build -t <name image web> .

3) Créer le container à partir de l'image <name image web>

        docker run -d --name <name container web> -p 8080:8080 --link <name container bdd> <name image web>
        
 ### Etape 3 : Affichage de l'application sur un navigateur
 
 Pour cela, vous devez rentrer l'url suivante dans un navigateur web : http://localhost:8080/dbproject/accueil.jsp

 
 
