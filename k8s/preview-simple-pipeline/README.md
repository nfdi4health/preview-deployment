# Install preview-pipeline


Install pipeline
```
helm upgrade preview-simple-pipeline  `
    --namespace="nfdi4health-preview"  `
    --set-string images.simplePipeline="ghcr.io/zbmed/preview-annotation-pipeline/autopipe:8f3de8b6adcf111b9c65e6d6de2406e7386aa20b"  `
    --set-string oidc.data_import.host="s3.de-west-1.psmanaged.com"  `
    --set-string oidc.data_import.bucket="preview-data"  `
IdeaProjects/preview-deployment/k8s/preview-simple-pipeline
```

Install manual jobs for simple-pipeline and add-publication-status (for testing)
```
kubectl -n nfdi4health-preview create job manual-data-pipeline --from cronjob/preview-simple-pipeline-data-pipeline
```

```
kubectl -n nfdi4health-preview create job manual-add-pub-status --from cronjob/preview-simple-pipeline-add-pub-status
```