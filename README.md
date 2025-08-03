# Grow With Saargunam – Static HTML on Minikube

This guide will help you deploy a static HTML page using NGINX on Kubernetes with Minikube.

## Prerequisites

- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Minikube](https://minikube.sigs.k8s.io/docs/)

## Steps

### 1. Start Minikube

```sh
minikube start
```

### 2. Create the ConfigMap for HTML Content

```sh
kubectl apply -f web-content.yaml
```

### 3. Deploy the Pod

```sh
kubectl apply -f pod.yaml
```

### 4. Expose the Pod via a Service

```sh
kubectl expose pod growwithsaargunam-pod --type=NodePort --port=80
```

### 5. Get the Service URL

```sh
minikube service growwithsaargunam-pod --url
```

This will output a URL like `http://127.0.0.1:XXXXX`.

### 6. View the Webpage

Open the URL from the previous step in your browser.  
You should see:

> **Grow With Saargunam 🚀**

---

**Cleanup:**

To delete all resources:

```sh
kubectl delete pod growwithsaargunam-pod
kubectl delete configmap web-content
```
