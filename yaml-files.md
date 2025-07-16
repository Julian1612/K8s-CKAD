# Yaml Files
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2 # tells deployment to run 2 pods matching the template
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80

```

Required fields for a manifest json 
## apiVersion
Which version of the Kubernetes API you're using to create this object

## kind
What kind of object you want to create
## metadata
Data that helps uniquely identify the object
### name
### UID
### namespacep

## spec
specifies the pod and its desired state (such as the container image name for each container within that pod).
