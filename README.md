* Install Argo CD

```sh
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

* Install Argo CD CLI

```sh
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64

sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd

rm argocd-linux-amd64
```

* Access the Aergo CD UI

```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Now the API server can be accessed at `127.0.0.1:8080`

* Get the default password

```sh
argocd admin initial-password -n argocd
```

Now access the dashboard with the following:

```
Username: admin
Password: <password_output>
```

* Initiate Argo CD with creating the project

```sh
kubectl apply -f sandbox/k8s/argocd.yaml
```
