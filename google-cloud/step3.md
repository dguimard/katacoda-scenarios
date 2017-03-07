Step 3

Load Balancing

https://cloud.google.com/compute/docs/load-balancing-and-autoscaling#network_load_balancing

Creation d'un network pour le load balancing

gcloud compute forwarding-rules create nginx-lb \
         --ports 80 \
         --target-pool nginx-pool

On peut executer un requete sur l'adresse ip indiquée par l'execution de cette commande
 http://IP_ADDRESS/ 
