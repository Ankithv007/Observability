# Install using Helm

## Add helm repo

`helm repo add grafana https://grafana.github.io/helm-charts`

## Update helm repo

`helm repo update`

## Install helm 

`helm install grafana grafana/grafana`

## Expose Grafana Service
`kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-ext`




### extra masala 
id port already taken
`lsof -i :<port number>`
`kill --9 <id of port>`

`kubectl get svc`
prometheus-server                     ClusterIP   10.105.156.252   <none>        80/TCP         7m26s id it is in cluster ip change into nodeport mode and than

`minikube service prometheus-server-ext`
prometheus-server-ext                 NodePort    10.100.97.215    <none>        80:32693/TCP   4m18s
that the name you have changed into nodeport 
