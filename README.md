# How to run 


Minikube runs in docker in default mode. I didn't have a good time with connecting to the services using minikube docker ingress. I even used tunnel but that too didn't work. What worked for me was starting the minikube using Virtual box as the driver. 

`minikube start --driver=virtualbox`

Next step is to enable Kong

`minikube addons enable kong`

Apply Kubernetes resources

`kubectl apply -f k8s/`

Check the service status and note the kong-proxy port.

`minikube service -n kong --all`

Then hit the service as follows. Use the port you got in the previous step.

`curl $(minikube ip):30481/foo`

`curl $(minikube ip):30481/bar`



