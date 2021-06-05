# GitHub Action Container to GCP



## Create Google Service Account

First step you have to create the GitHub Account to access the Google Cloud 
Container Registry

```
gcloud iam service-accounts create github-actions --display-name="GitHub" \
  --project <project name>
```

Add storage admin role

```
gcloud projects add-iam-policy-binding <project name>\
  --member='serviceAccount:github-actions@<project name>.iam.gserviceaccount.com' \
  --role='roles/storage.admin'
```

Create the JSON secret
```
gcloud iam service-accounts keys create \
  --iam-account=github-actions@<google project>.iam.gserviceaccount.com \
  serviceAccount.json
```
