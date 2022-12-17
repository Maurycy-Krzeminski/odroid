First run:

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.6.1/aio/deploy/recommended.yaml
```

Afterwards run:

```
kubectl create -f dashboard.admin-user.yml -f dashboard.admin-user-role.yml
```


to get token run:
```
kubectl -n kubernetes-dashboard create token admin-user
```


to access dashboard run:
```
kubectl proxy
```
and go to [here](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/)
