# How to deploy to GKE

## Resources
[https://www.tinfoilcipher.co.uk/2020/06/09/deploying-to-google-kubernetes-engine-using-helm/](https://www.tinfoilcipher.co.uk/2020/06/09/deploying-to-google-kubernetes-engine-using-helm/)

## Fetch cluster staging
`
gcloud container clusters get-credentials supertoken-core --zone europe-west1 --project igneous-thunder-236214
`

## Fetch cluster production
`
gcloud container clusters get-credentials supertoken-core --zone europe-west1 --project rentack-backend-production
`
## Deploy
`helm install/upgrade supertokens ./helm-chart  --values ./helm-chart/values-prod/staging.yaml`

## How to setup  a new environment
- Create a new cluster in GKE
- deploy it with helm install
- create a new SQL cloud instance
  - create a new database "supertokens"
  - enable private IP
  - create a new user "supertoken"
- Set in the value.yaml the new SQL instance private IP and the new user credentials
- Go to "IP adresses" in google cloud and turn ip adress assigned to the ingress to a static ip then add a A record 
  with the subdomain you want to use with the value of the static IP
