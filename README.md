# BubbleNiort


##Des les liens vers de la doc :
https://prometheus.io/docs/introduction/overview/
https://grafana.com/
https://coreos.com/blog/the-prometheus-operator.html
https://coreos.com/operators/prometheus/docs/latest/user-guides/getting-started.html
https://coreos.com/operators/prometheus/docs/latest/
https://github.com/prometheus/node_exporter
https://github.com/kubernetes/kube-state-metrics/
https://kubernetes.io/docs/getting-started-guides/minikube/
https://docs.docker.com/engine/installation/
http://blog.cloud66.com/how-to-create-the-smallest-possible-docker-image-for-your-golang-application/
https://www.habitus.io
## De quoi rejouer la démo du 30/05/2018
### Prérequis
  - minikube installé : https://kubernetes.io/docs/tasks/tools/install-minikube/
  - et docker !!! 

### Start de minikube (en fonction de votre machine ...)
minikube start --cpus 6 --memory 4096

### Compilation et dockerisation
```
docker build -f Dockerfile.builder -t builder:latest .
docker run builder
docker ps -all
docker build -f Dockerfile.multiStageBuild -t marcdivet01/bubble:v001 .
docker login 
docker push votrerepo/bubble:v001

```
### Bootstrap du cluster
kubectl create -f 1PromOperateur.yaml
```
   --> attendre que le pod de prometheus-operator est bien démaré avant la suite ;-)
kubectl create -f 2BootStrapBubble.yaml
```
### Déploiment des 2 microservices
kubectl create -f 3deployMicSrvPersonne.yaml
kubectl create -f3deployMicSrvPersonne.yaml
```
### Démarage des consoles
```
minikube dashboard
minikube service prometheus
minikube service graphana
```
### Configuration de grafana
ajout de la data source : nom --> PrometheusLocalHost url --> http://prometheus:9090
upload des 3 tableaux de bord :
  - Cluster Cockpit-1508946335336.json
  - MicroSrv-1508947462976.json
  
 # ENJOY !
