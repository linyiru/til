# Updating Kubernetes ConfigMap and Secrets without removing the existing one

Kubernetes ConfigMap & Secrets are both really useful for managing environment variables and credentials.

You can create a cnofigmap from shell easily:

```shell
kubectl create configmap app-config --from-env-file ./.env.production
```

If you wanna change the configuration in configmap, you can just edit it from command line as well:

```shell
kubectl edit configmap admin-config
```

Very nice and easy. 
