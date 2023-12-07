# uds-package-irsa

Deploy the Amazon EKS pod identity webhook for IAM Roles for Service Accounts (IRSA).

This Zarf Package is primarily sourced from this [guide from AWS](https://github.com/aws/amazon-eks-pod-identity-webhook/blob/master/SELF_HOSTED_SETUP.md) for deploying the [Amazon EKS Pod Identity Webhook](https://github.com/aws/amazon-eks-pod-identity-webhook#in-cluster) in self-hosted clusters.

The package is comprised of three Helm Charts

1. [certgen](charts/certgen/) - generate the certificate with cert-manager
1. [webhook](charts/webhook/) - deploy the webhook
1. [patch](charts/patch/) - patch the webhook with the cert from cert-manager

*Note: this package uses [YOLO Mode](https://docs.zarf.dev/examples/yolo/) and assumes you have access to the  images listed below*

* k8s.gcr.io/ingress-nginx/kube-webhook-certgen:v1.3.0
* amazon/amazon-eks-pod-identity-webhook:v0.5.2

## Prerequisites

* Kubernetes cluster >= v1.24
* Zazf >= v0.31.2

## Create

```bash
zarf package create
```

## Deploy

Do not `zarf init` prior to deploying this package

```bash
zarf package deploy zarf-package-pod-identity-webhook-*.tar.zst
```

## Remove

```bash
zarf package remove zarf-package-pod-identity-webhook-*.tar.zst --confirm
```
