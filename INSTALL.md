# **Qlik Sense Enterprise for Kubernetes em Minikube** (Ambiente de Teste)

## Instalação do Qlik Sense Enterprise for Kubernetes

### Criação do YAML com configurações para o Qlik Sense Enterprise for Kubernetes

Crie o arquivo values.yaml com o conteúdo abaixo e salve no diretório C:\Minikube ou ~\Minikube

```yaml
#Esta configuração ativa o modo desenvolvimento e inclui uma instalação local de MongoDB
devMode:
  enabled: true


engine:
  #Esta configuração aumenta o limite de upload do NGINX para 5 GB 
  ingress:
    annotations:
      nginx.ingress.kubernetes.io/proxy-body-size: 5000m
      nginx.org/client-max-body-size: 50000m
  #Esta configuração aceita os termos de licenciamento (EULA) do produto
  acceptEULA: "yes"

elastic-infra:
  #Esta configuração aumenta o limite de upload do NGINX para 5 GB
  ingress:
    annotations:
      nginx.ingress.kubernetes.io/proxy-body-size: 50000m
      nginx.org/client-max-body-size: 50000m
  #Configuração específica para o Minikube (não utilize com outros provedores K8S)
  nginx-ingress:
    controller:
      service:
        type: NodePort
        nodePorts:
          https: 32443
      extraArgs.report-node-internal-ip-address: ""
  #Esta configuração aumenta o limite de upload do NGINX para 5 GB
  ingress:
    annotations:
      nginx.ingress.kubernetes.io/proxy-body-size: 50000m
      nginx.org/client-max-body-size: 50000m

hub:
 ingress:
   annotations:
     nginx.ingress.kubernetes.io/auth-signin: https://$host:32443/login?returnto=$request_uri

management-console:
 ingress:
   annotations:
     nginx.ingress.kubernetes.io/auth-signin: https://$host:32443/login?returnto=$request_uri

edge-auth:
  oidc:
    redirectUri: https://elastic.example:32443/login/callback
```

### Instalação do Qlik Sense

Adicione o repositório da Qlik no helm

```sh
helm repo add qlik https://qlik.bintray.com/stable
```

Atualize os repositórios do helm

```sh
helm repo update
```

Instale o pacote inicial do Qlik Sense

```sh
helm install --name qliksense-init qlik/qliksense-init
```

Instale o Qlik Sense utilizando o values.yaml que foi criado anteriormente

```sh
helm install -n qliksense qlik/qliksense -f values.yaml
```

### Adicione o IP do Minikube no arquivo de hosts

Para obter o IP do Minikube execute o comando:

```sh
minikube ip
```

Localize o arquivo de hosts e faça a inclusão do IP do Minikube para o DNS elastic.example.

A entrada deve ser feita conforme exemplo:
35.247.193.178 elastic.example

Windows - %SYSTEMROOT%\System32\drivers\etc\hosts

Unix - /etc/hosts


### [Próximo -> Pós instalação](PINSTALL.md)

### [Voltar <- Provisionando o ambiente](PROVISIONING.md)

### [Tabela de conteúdo](README.md)