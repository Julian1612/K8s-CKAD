# K8s-CKAD
creates the Kubernetes objects (like Pods, Services, or Deployments) defined within it
```Bash
k create -f <file>.yml
```
Create a new resource from a definition file
```Bash
k apply -f </path/to/file/file.yaml>
```
forcefully replaces a Kubernetes resource by first deleting the existing one and then immediately recreating it using the configuration from the simple-webapp-2.yaml file.
```Bash
kubectl replace -f simple-webapp-2.yaml --force
```
Dieser Befehl zeigt den Inhalt der Datei /log/app.log aus dem Pod namens app im elastic-stack Namespace an.
```Bash
kubectl -n elastic-stack exec -it app -- cat /log/app.log
```
## Use --dry-run-client to get a minimalistic yaml with only the neccesery defintions

## Usefull Shell commands
Use grep to search for words in the outputted text like strg + f
```Bash
k describe pod mosquito | grep "Node"
```
## Usefull vim commands
delete the entire content of a page (or file)
`:%d`

## Pod
Erstellt einen neuen Pod aus einem Image
```Bash
k describe pod <Pod name>
```
Listet alle Pods im aktuellen Namespace auf
```Bash 
k get pods
```
Modify the properties of the pod
```Bash
kubectl edit pod <pod-name>
```
Create new pod with image
```Bash
kubectl run my-nginx --image=nginx
kubectl run nginx --image=nginx --dry-run=client -o yaml
```
Extract the definition to a file
```Bash
kubectl get pod <pod-name> -o yaml > pod-definition.yaml
```
## ReplicaSets
List all available replicasets
```Bash
k get replicasets
```
Delete a replicaSets
```Bash
k delete replicaset <Name of the replicaSet>
```
## Deployment

```Bash
kubectl create deployment --image=nginx nginx
```
Generate Deployment YAML file (-o yaml). Don't create it(--dry-run)
```Bash
kubectl create deployment --image=nginx nginx --dry-run -o yaml
```
```Bash
kubectl create deployment nginx --image=nginx --replicas=4
kubectl create deployment nginx --image=nginx--dry-run=client -o yaml > nginx-deployment.yaml
```
## Service
```Bash
kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml
```
```Bash
kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml
```
```Bash
kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml
```

## Imerative Commands
as soon as the command is run, the resource will be created. If you simply want to test your command, use the --dry-run=client option. This will not create the resource. Instead, tell you whether the resource can be created and if your command is right.
```Bash
--dry-run
--dry-run=client
```
will output the resource definition in YAML format on the screen.
```Bash
-o yaml
```
```Bash
kubectl run nginx --image=nginx --dry-run=client -o yaml > nginx-pod.yaml
```
## ConfigMaps
Create without a file and add all the infomations manually, the imerative way
```Bash
kubectl create configmap \
  app-config --form-literal=APP_COLOR=blue \
             --from-literal=APP_MOD=prod
```
```Bash
kubectl create configmap \
  <config-name> -- form-file=<path-to-file>
```
Create CM with a file (First create the File)
```Bash
kubectl create -f <file-name>.yaml
```
## Secrets
imperative
```Bash
kubectl create secret generic app-secret --from-literal=DB_Host=mysql --from-literal=DB_User=root --from-literal=DB_Pass=mpaswrd
```
Declarative -> create a file and apply
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
data:
  DB_Host: mysql
  DB_User: root
  DB_Pass: paswrd 
```
## Serviceaccounts
Create a sa
```Bash
kubectl create serviceaccount dashboard-sa
```
 listet dann die Dateien im Verzeichnis auf, in dem die Anmeldeinformationen des Service-Accounts des Pods gespeichert sind.
```Bash
k exec -it my-kubernetes-dashboard ls /var/run/secrets/kubernetes.io/serviceaccount
```
```Bash
k exec -it my-kubernetes-dashboard cat /var/run/secrets/kubernetes.io/serviceaccount
```
Dieser Befehl weist der Kubernetes-Deployment namens web-dashboard den Service-Account dashboard-sa zu.
```Bash
kubectl set serviceaccount deploy/web-dashboard dashboard-sa
```
## Taints
fügt einem Kubernetes-Knoten einen "Taint" hinzu, der verhindert, dass Pods ohne eine passende "Tolerierung" auf diesem Knoten geplant werden oder dort verbleiben.
```Bash
kubectl taint nodes node-name key=value:taint-effect
```
## Label Nodes
Dieser Befehl fügt dem Kubernetes-Knoten mit dem Namen node-1 ein Label hinzu, das ihn mit size=Large kennzeichnet.
```Bash
kubectl label nodes <node-name> <label-key>=<label-value>
e.g kubectl label nodes node-1 size=Large
```

## Rollouts
Überwacht und zeigt in Echtzeit den Fortschritt des Updates für das Kubernetes-Deployment namens myapp-deployment an, bis es erfolgreich abgeschlossen ist.
```Bash
k rollout status deployment/myapp-deployment
```

Zeigt die gesamte Änderungshistorie mit allen bisherigen Versionen (Revisionen) des Kubernetes-Deployments myapp-deployment an.
```Bash
k rollout history deployment/myapp-deploy
```




