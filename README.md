# GitHub Action Container to GCP


## Prerequisites

Set up the following resources manually in the Cloud Console
or use a tool like [Terraform](https://www.terraform.io).

* Create a [Google Cloud](https:console.cloud.google.com) Project
* Enable Container Registry API
* Create Service Account with Role `Storage Admin` and export a new JSON key.
  * First step you have to create the GitHub Account to access the Google Cloud 
Container Registry
```
gcloud iam service-accounts create github-actions --display-name="GitHub" \
  --project <project name>
```
  * Add storage admin role
```
gcloud projects add-iam-policy-binding <project name>\
  --member='serviceAccount:github-actions@<project name>.iam.gserviceaccount.com' \
  --role='roles/storage.admin'
```
  * Create the JSON secret
```
gcloud iam service-accounts keys create \
  --iam-account=github-actions@<google project>.iam.gserviceaccount.com \
  serviceAccount.json
```

## Github Action Inputs

| Variable                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| `credentials`                    | ***Required*** Service Account JSON Key (not base64 encoded)                |
| `project`                        | ***Required*** Google Cloud project name                                    |
| `image`                          | ***Required*** Container image name                                         |

