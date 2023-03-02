# CloudRAN Challenge

## minikube Deployment
Clone this repo. This assumes Kubernetes has been set up with minikube and minikube has been started with `minikube start`.

To deploy the app, run
```
kubectl apply -f <path/to>/deploy-hello-app.yaml
```

Expose the service.
```
kubectl expose deployment hello-app --port=8080 --type=NodePort
```

Forward the port so the service is accessible on port 8080. 
```
kubectl port-forward service/hello-app 8080:8080
```

Get the ip of the service. 
```
minikube service hello-app --url
```

Now, test it using curl. 
```
curl http://<ip>:8080
```


## Helm instructions

After installing Helm, create and deploy the packaged application. 
```
helm install <desired name> <path/to>/hello-app-chart-0.1.0.tgz
```

Expose the service and forward the port (again).
```
kubectl expose deployment hello-app-<name> --port=8080 --type=NodePort
kubectl port-forward deploy/hello-app-<name> 8080:8080
```

Run and get the IP for the service.
```
minikube service hello-app-<name> --url
```

Test the service as desired using curl.
