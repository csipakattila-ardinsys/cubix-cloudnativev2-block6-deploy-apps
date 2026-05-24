# Cubix Cloud-Native Application Development Training: cloud-native requirements (app deployment)

Fork this repository for the practice session.

# How to start the api application

```shell
helm upgrade api spring-cubix --install -f api.yaml -n cubix
```

# How to start the db application

Replace password (with the value of Postgres password)

```shell
#helm upgrade db spring-cubix --install -f db.yaml -n cubix --set env[2].value=<ENTER-PASSWORD>
kubectl create secret generic db-password --from-literal password=password --namespace cubix --save-config
kubectl label secret/db-password app.kubernetes.io/instance=db --namespace cubix
helm upgrade db spring-cubix --install -f db.yaml -n cubix
```

# How to label the namespace for monitoring

```shell
kubectl label ns/cubix monitoring=true
```
