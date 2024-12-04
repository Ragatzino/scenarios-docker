
Dans cette partie nous allons voir comment construire des images a partir d'autres images.


Voici le dockerfile que nous allons utiliser pour l'installation : 

```Dockerfile
# Utilise l'image officielle Tomcat
FROM tomcat:10-jre21

# Télécharge le fichier WAR depuis une URL
RUN curl -o /usr/local/tomcat/webapps/app.war https://tomcat.apache.org/tomcat-10.0-doc/appdev/sample/sample.war

# Expose le port 8080
EXPOSE 8080

# Commande pour démarrer Tomcat
CMD ["catalina.sh", "run"]
```

Créez ce Dockerfile dans /root/Dockerfile

`
touch /root/Dockerfile
`{execute}


**Création du livrable : l'image Docker**
> A partir d'un Dockerfile localisé dans un repertoire /dir/ on peut construire une image docker

Utilisez la commande suivante pour construire l'image Docker :

`
docker build -t tomcat-with-war .
`{execute}

> L'option -t génère un tag pour l'image, par défaut latest, si vous désirez taguer l'image avec une vraie valeur, ajoutez **:v1** ou autre


**Vérifications**

Vous pouvez vérifier que votre image est bien construite

`
docker image list
`{execute}


La lancer

`
docker run -d --name montomcatavecwar -p 8080:8080 tomcat-with-war
`{execute}


Et vérifier qu'elle tourne bien :

`
curl -vv localhost:8080/app
`{execute}

