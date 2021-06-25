# k8s-mattermost

## To build mattermost
```
$ minikube start

$ helm repo add mattermost https://helm.mattermost.com
$ helm repo update
$ helm install my-release mattermost/mattermost-team-edition \
  --set mysql.mysqlUser=sampleUser \
  --set mysql.mysqlPassword=samplePassword \


$ minikube kubectl get pods
NAME                                                 READY   STATUS    RESTARTS   AGE
my-release-mattermost-team-edition-866bfb85d-tsmdd   1/1     Running   0          10m
my-release-mysql-845688746c-wpjlp                    1/1     Running   0          10m


# Run Server  
$ kubectl port-forward --namespace default $(kubectl get pods --namespace default -l "app.kubernetes.io/name=mattermost-team-edition,app.kubernetes.io/instance=my-release" -o jsonpath='{ .items[0].metadata.name }') 8080:8065

```
