# Yaml Files

### First of all
the number of spaces doesn’t matter — as long as it’s at least 1, and as long as you’re CONSISTENT.
For example, name and labels are at the same indentation level, so the processor knows they’re both
part of the same map; it knows that app is a value for labels because it’s indented further.

**Quick note: NEVER use tabs in a YAML file.**

There are only two types of structures you need to know about in YAML:
### Maps
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: rss-site
  labels:
    app: web
```

### Lists
```yaml
args:
  - sleep
  - "1000"
  - message
  - "Bring back Firefly!"
```

We have:
- maps, which are groups of name-value pairs
- lists, which are individual items
- maps of maps
- maps of lists
- lists of lists
- lists of maps

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
What kind of object you want to create (Pod, Deployment, Job, Service...)
## metadata
Data that helps uniquely identify the object, specifying the name of the Pod, as well as the label we’ll use to identify the pod.
***- name
- UID
- namespace***

## spec
specifies the pod and its desired state (such as the container image name for each container within that pod).


## Pod yaml
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
```

### Source:
https://www.mirantis.com/blog/introduction-to-yaml-creating-a-kubernetes-deployment/
