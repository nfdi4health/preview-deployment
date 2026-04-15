# Install preview UI

- create imagePullSecret regcred
- create s3-secrets:
```
kubectl -n nfdi4health-preview create secret generic preview-s3-key --from-literal=preview-s3-key='abc'
kubectl -n nfdi4health-preview create secret generic preview-s3-keyid --from-literal=preview-s3-keyid='XYZ'
```

Install on QA cluster:
```
helm install nfdi4health-preview  `
    --namespace="nfdi4health-preview"  `
    --set-string images.backend="ghcr.io/nfdi4health/preview/backend:6bdb18f0e0e474fa1a8aca01fe9aa19491b6aa8e"  `
    --set-string images.frontend="ghcr.io/nfdi4health/preview/frontend:8f619b8f889f3b06b13a4dd2bec38d626db77284"  `
    --set-string ingress.dns="preview.qa.km.k8s.zbmed.de"  `
    --set-string oidc.data_import.host="s3.de-west-1.psmanaged.com"  `
    --set-string oidc.data_import.bucket="preview-data"  `
    --set-string oidc.backend.elasticindex="hub1"  `
IdeaProjects/preview-deployment/k8s/preview
```

Start manual import job (for testing):
```
kubectl -n nfdi4health-preview create job manual-import --from cronjob/nfdi4health-preview-backend-data-import
```

