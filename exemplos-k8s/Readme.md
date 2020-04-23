 
# Material suplementar para Palestra de Kubernetes

Neste repositório encontrara alguns exemplos para treinar seu conhecimento referente a Kubernetes.
Apresentaremos três exemplos.

* Docusaurus - Website e blog
* NGinx - HTTP Server/Proxy
* PostgreSQL - Banco Opensource Relacional

| Serviços | Diretórios |
| ------   | ------     |
| Docusaurus | ./docusaurus|
| NGinx | ./nginx |
| PostgreSql | ./postgresql

Na raiz do projeto encontra-se os arquivos originais referente ao projeto [Docusaurus](https://docusaurus.io/)


## Explicação dos arquivos de configuração
A idéia é ter esse documento como base pois a idéia é detalher e tirar as dúvidas na palestra.

**Deployment.yaml**

```sh
apiVersion: apps/v1                               # Define a versão do Schema do objeto
kind: Deployment                                  # Representa o recurso neste caso Deployment 
metadata:                                              
  name: docusaurus                                # Nome da aplicação
spec:                                             # Especificações do comportamento desejado na implantação
  replicas: 5                                     # Defini a quantidades de réplicas
  selector:                                       # Seletor defini as implantações e localiza os pods a gerenciar
    matchLabels:                                  # Mapa de pares "Chave e valor"
      app: docusaurus                             # O rótulo definido
  template:                                       # O template de definições do Pod/container
    metadata:                                     
      labels:                                     # rótulo           
        app: docusaurus                           # selecionando o rótulo do pod
    spec:                                         # especificações do template
      containers:                                 # Container properties
        - name: docusaurus                        # nome do container
          image: robisongarcia/docusaurus:1.0.0   # imagem a ser utilizada
          ports:                                  # 
            - containerPort: 3000                 # Tipo de serviço setando porta do container neste caso 3000/TCP
          imagePullPolicy: Always                 # Por padrão é setado se a imagem existir não baixar, esta opção força atualização.
```


**Service.yaml** 


```sh
apiVersion: v1                                    # Versão do tipo do Recurso
kind: Service                                     # Tipo Service 
metadata:
  name: docusaurus                                # Nome do Service
spec:                                             # Especificações do Service
  selector:                                       # 
    app: docusaurus                               # Seleciona os pods com os dados especificados        
  ports:                                          #
    - port: 80                                    #      
      targetPort: 3000                            # TargetPort escuta na porta 80 e faz a ponte e redireciona para a porta do container 3000  
  type: LoadBalancer                              # Type Loadbalancer torna os pods expostos acessíveis fora do cluster, por default ClusterIP
```

## Comandos 
 
**Subindo**
```sh
kubectl apply -f .
```

**Mostrar pods,services e deployments filtrando por seletor**
```sh
kubectl get po,svc,deploy --selector app=docusaurus
```

**Escalando**
```sh
kubectl scale --replicas=10 deployment docusaurus
```

**Acompanhando**
```sh
kubectl rollout status deployment.v1.apps/docusaurus
```

**Trocando imagem**
```sh
kubectl set image deployment/docusaurus app=robisongarcia/docusaurus:2.0.0
```

**Verificando historico de distribuição de uma imagem**
```sh
kubectl rollout history deployment.v1.apps/docusaurus
```

**Rollback**
```sh
kubectl rollout undo deployment.v1.apps/docusaurus
```

**Descrição da implantação** 
```sh
kubectl describe deployment docusaurus
```

**Verificando pods,services,deployments com o Seletor docusaurus**
```sh
kubectl get po,svc,deploy --selector app=docusaurus
```
**Apagando pods,services,deployments com o Seletor docusaurus**
```sh
kubectl delete po,svc,deploy --selector app=docusaurus
```