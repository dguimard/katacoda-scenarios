Step 2

Preparation du cluster

`gcloud config set compute/zone us-central1-f`

`gcloud config set compute/region us-central1`

## Creation d'un fichier de boot pour nginx

#! /bin/bash
apt-get update
apt-get install -y nginx
service nginx start
sed -i -- 's/nginx/Google Cloud Platform - '"$HOSTNAME"'/' /var/www/html/index.nginx-debian.html
 

gcloud compute instances create nginx --metadata-from-file startup-script=startup.sh 

##  1 - Creation d'une instance template
gcloud compute instance-templates create nginx-template --metadata-from-file startup-script=startup.sh


## 2 - Créons un pool cible. Un pool cible nous permet d'avoir un seul point d'accès à toutes les instances d'un groupe et 
est nécessaire pour l'équilibrage de charge dans les étapes futures.
gcloud compute target-pools create nginx-pool



gcloud compute instance-groups managed create nginx-group \
         --base-instance-name nginx \
         --size 2 \
         --template nginx-template \
         --target-pool nginx-pool



finallement,
gcloud compute instances list
