# Rotten Potatoes

Aplicação web da [Iniciativa Kubernetes](https://iniciativakubernetes.com.br/) para utilização do Kubernetes no deploy de uma aplicação de listagem de filmes.

## Etapas para execução

1. Clonar o repositório:

```
$ git clone https://github.com/lucasfusinato/rotten-potatoes

$ cd rotten-potatoes
```

2. Construir a imagem:

```
$ docker build -t kubedev/rotten-potatoes:1.0 -f src/Dockerfile src/
```

3. Criar um Container Registry local:

```
$ docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

4. Enviar imagem para o Container Registry local:

```
$ docker tag kubedev/rotten-potatoes:1.0 localhost:5000/kubedev/rotten-potatoes:1.0

$ docker push localhost:5000/kubedev/rotten-potatoes:1.0
```

5. Execução com Kubernetes:

```
$ kubectl apply -f k8s/mongodb-deployment.yaml

$ kubectl apply -f k8s/rotten-potatoes-deployment.yaml
```

4. Testar a aplicação:

```
$ curl -X GET "http://localhost:30020/health"
```

E pronto! O resultado do último comando deverá apresentar "OK". Também deve ser possível testar a aplicação através da [interface web](http://localhost:30020).