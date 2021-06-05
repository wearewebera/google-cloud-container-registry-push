# GitHub Action Container to GCP



## Create Google Service Account

First step you have to create the GitHub Account to access the Google Cloud 
Container Registry

```
gcloud iam service-accounts create github-actions --display-name="GitHub"
```

Add storage admin role

```
gcloud projects add-iam-policy-binding <google project>\
  --member='serviceAccount:github-actions@<google project>.iam.gserviceaccount.com' \
  --role='roles/storage.admin'
```

Create the JSON secret
```
gcloud iam service-accounts keys create \
  --iam-account=github-actions@<google project>.iam.gserviceaccount.com \
  serviceAccount.json
```
