# Docker run

L'utilisation de docker se limite a quelques cas : 
- Création d'images nouvelles a partir de fichier **blueprint** Dockerfile
- Lancement d'images docker existantes
- Déploiement d'images sur un registre d'images **docker push**

L'objectif de cette partie est l'execution d'images pour découvrir docker.

Commençons par executer une image docker de base : 

`
docker run hello-world
`{{execute}}

Cette image décrit tout le déroulement de sa récupération a son execution.

*Quelques options*

**Choisir sa version :** 

Le numéro après le **:** permet de définir la version. (voir https://hub.docker.com/_/tomcat) par exemple tomcat:10-jre21 => 10-jre21 = java 21, tomcat 10.

Des versions plus légères (slim) existent également.

**Choix du port :** 

L'option -p permet de définir le port sur la machine hote ouvert sur le conteneur : un tomcat exposant sur le port 8080 par défaut

`
docker run --name tomcat1 -p 8080:8080 tomcat:10-jre21
`{{execute}}

> Cela expose le port 8080 du conteneur vers le port 8080 de la machine.


**Lancer un conteneur en tache de fond:** 

L'option -d permet de lancer un conteneur sur la machine en arrière plan.
=> Cette option fait que l'on retourne l'id du conteneur

`
docker run -d --name tomcat2 -p 8888:8080 tomcat:10-jre21
`{{execute}}


**Consultez les images qui tournent**

`
docker ps
`{{execute}}

## Exécuter du code sur un conteneur
Vous pouvez executez du code sur des conteneurs avec la commande **exec**
et l'option -it permet de passer en mode interactif sur une conteneur

Il est de la forme :
`
docker exec ID_CONTENEUR <commande-dans-le-conteneur>
`

> Cela renvoie le resultat sur la machine hôte: notre ubuntu ici.

**Testez par exemple:**

`
docker exec tomcat2 cat README.md
`{{execute}}

`
docker exec -it tomcat2 bash
`{{execute}}

- (ne fonctionne que si l'image à bash, évidemment)
