# AWS SSM Secret Operator

> A Kubernetes Operator to automatically create and manage Kubernetes Secrets from AWS SSM Parameter Store.

---

## ✨ Overview

`aws-ssm-secret-operator` lets you declare external secrets from AWS Parameter Store using Kubernetes-native Custom Resources (`AwsSecret`). It securely fetches SSM parameters and synchronizes them into Kubernetes secrets — perfect for DevOps teams leveraging AWS-native secrets management.

---

## 📦 Features

- 🔒 Pull secrets from AWS SSM Parameter Store
- 🔁 Auto-create and update Kubernetes secrets
- 🔄 Periodic reconciliation and manual sync
- 💥 Finalizer support for cleanup (optional)
- 🔍 CRD validation and status conditions

---

## 🧱 Custom Resource Definition (CRD)

```yaml
apiVersion: secrets.mohibul.dev/v1alpha1
kind: AwsSecret
metadata:
  name: my-db-secret
  namespace: default
spec:
  secretName: my-db-secret
  region: us-east-1
  decrypt: true
  parameters:
    - name: /myapp/db-username
      key: username
    - name: /myapp/db-password
      key: password
