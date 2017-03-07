Step 4
## Cleanup
`gcloud compute forwarding-rules delete nginx-lb`

`gcloud compute instance-groups managed delete nginx-group`

`gcloud compute target-pools delete nginx-pool`

`gcloud compute instance-templates delete nginx-template`

`gcloud compute instances delete iki-1`

`gcloud compute instances delete nginx`

`gcloud compute firewall-rules delete allow-80`
