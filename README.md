# Rotten Potatoes

Aplicação web da [Iniciativa Kubernetes](https://iniciativakubernetes.com.br/) para utilização do Kubernetes no deploy de uma aplicação de listagem de filmes.

```
$ git clone https://github.com/lucasfusinato/rotten-potatoes

$ cd rotten-potatoes
```

## Etapas para execução com Kubernetes

1. Criar o *deployment*:

```
$ kubectl apply -f k8s/mongodb-deployment.yaml

$ kubectl apply -f k8s/rotten-potatoes-deployment.yaml
```

2. Testar a aplicação:

```
$ KUBERNETES_HOST=localhost

$ curl -X GET "http://$KUBERNETES_HOST:30020/health"
```