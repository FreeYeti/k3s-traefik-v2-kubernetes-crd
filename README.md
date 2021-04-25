# k3s + Traefik v2.x

## Original readme

* [https://github.com/sleighzy/k3s-traefik-v2-kubernetes-crd#readme](https://github.com/sleighzy/k3s-traefik-v2-kubernetes-crd#readme)

## Install Traefik v2.x Kubernetes CRD Ingress Controller

### version

```bash
k3s version v1.20.5+k3s1 (355fff30)
go version go1.15.10
```

### Traefik

- [001-crd.yaml] - CRDs - adapt to k8s v1.22.0+
- [002-rbac.yaml] - cluster roles
- [003-tls-options.yaml] - enforces by default that TLS 1.2 is to be
  used for secure connections
- [006-service.yaml] - exposes the container ports for traefik
- [007-service-account.yaml] - create service account for traefik
- [008-deployment.yaml] - the deployment of the Traefik container with the
  associated mounts for secrets and persistent volume if integrating with
  LetsEncrypt for https certificates
  don't forget to change the email address and local path

### Traefik Dashboard


- [102-middlewares-secure-headers.yaml] - this creates a middleware
  that can be used to set secure headers on responses
- [103-middlewares-https-redirection.yaml] - redirect http to https
- [104-middlewares-basic-auth.yaml] - provides username / password
  authentication and is used in these examples for securing the Traefik
  dashboard using Basic Authentication
- [105-secrets.yaml] - (optional), but is needed if
  - using Basic Authentication for the dashboard
  - integrating with LetsEncrypt (depending on your mechanism) for API keys etc.
    for your DNS provider as per the examples further down
    default user: testuser, password: 123456
- [106-dashboard-ingressroute.yaml] - (optional), can be used to expose the Traefik
  dashboard externally and secure using Basic Authentication
