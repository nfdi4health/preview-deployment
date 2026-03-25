# Install preview
```
helm install my-test ./preview
```

```
helm install nfdi4health-preview  `
    --namespace="nfdi4health-preview"  `
    --set-string images.backend="ghcr.io/nfdi4health/preview/backend:8f619b8f889f3b06b13a4dd2bec38d626db77284"  `
    --set-string images.frontend="ghcr.io/nfdi4health/preview/frontend:8f619b8f889f3b06b13a4dd2bec38d626db77284"  `
    --set-string ingress.dns="preview.qa.km.k8s.zbmed.de"  `
    --set-string oidc.data_import.host="s3.de-west-1.psmanaged.com"  `
    --set-string oidc.data_import.bucket="preview-data"  `
    --set-string oidc.backend.elasticindex="hub1"  `
IdeaProjects/preview-deployment/k8s/preview
```