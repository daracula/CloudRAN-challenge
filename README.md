# CloudRAN Challenge

This assumes Kubernetes has been set up with minikube and minikube has been started.

To set up deployment, run 
`kubectl apply -f deploy-hello-app.yaml`

Expose the service.
`kubectl expose deployment hello-app --port=8080 --type=NodePort`

Forward the port so the service is accessible on port 8080. 
`kubectl port-forward service/hello-app 8080:8080`

Get the ip of the service. `minikube service hello-app --url`

Now, test it using curl. `curl http://<ip>:8080`
