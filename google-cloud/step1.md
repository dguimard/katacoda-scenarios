Step 1

## Task

Création d'une instance de Compute Engine

`gcloud compute instances create myinstance`

Activer le pare-feu pour le port 80

`gcloud compute firewall-rules create allow-80 --allow tcp:80`

SSH installation

`gcloud compute ssh myinstance`

Installation de Nginx

`sudo su -`

`apt-get update`

`apt-get install -y nginx``

`service nginx start

`exit`

Test
wget -q -O - localhost:80