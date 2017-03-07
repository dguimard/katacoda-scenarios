Step 5

## Création du Kubernetes Cluster
`gcloud container clusters create iki --num-nodes 3`

## NGINX dans Kubernetes

`kubectl run nginx --image=nginx --replicas=3`

Cela va créer un contrôleur de réplication pour faire tourner jusqu'à 3 pods, chaque pod s'exécute le conteneur NGINX. Vous pouvez voir l'état du déploiement en exécutant:


`kubectl get pods -owide`

Une fois que tous les pods ont l'état Exécution, vous pouvez ensuite exposer le cluster NGINX en tant que service externe

`kubectl expose deployment nginx --port=80 --target-port=80 --type=LoadBalancer`

Cette commande créera alors un network load balancer  pour charger le load balanceur aux trois instances NGINX. Pour trouver l'adresse de l'équilibreur de charge réseau , il faut taper la commande suivante :

`kubectl get service nginx`


Vous pouvez ensuite visiter http: // EXTERNAL_IP / pour voir le serveur!
