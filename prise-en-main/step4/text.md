Une fois qu'on a construit une image en local on veut la déployer.

L'objectif de cette partie est de déployer notre image sur le registry local `local-registry:5000`.


**La norme est de taguer l'image localement au registry cible :** 

`
docker tag tomcat-with-war local-registry:5000/tomcat-with-war
`{{execute}}

`
docker tag tomcat-with-war:1.0.0 local-registry:5000/tomcat-with-war:1.0.0
`{{execute}}


**Puis de la pusher**

`
docker push local-registry:5000/tomcat-with-war
`{{execute}}


> Dans les faits il y a souvent une authentification : **docker login**. On approfondira pas plus.

