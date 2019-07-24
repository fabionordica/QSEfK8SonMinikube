# **Qlik Sense Enterprise for Kubernetes em Minikube** (Ambiente de Teste)

## Provisionando o ambiente

### Criação do Minikube

Abra o PowerShell / Terminal em modo administrador / root, altere os parâmetros de tamanho de memória e quantidade (sendo o mínimo de 8GB de RAM e 2 CPUs).

```sh
minikube start --memory tamanho-memoria-em-mb --cpus quantidade-de-cpus
```

Exemplo:

```sh
minikube start --memory 8000 –cpus 2
```

### IP do Minikube

Para obter o IP do Minikube execute o comando:

```sh
minikube ip
```

### Configuração do kubectl

Para se certificar que o kubectl está utilizando o minikube utilize o seguinte comando:

```sh
kubectl config use-context minikube
```
### Diretório para arquivos YAML
Crie o diretório C:\Minikube ou ~\Minikube.

### RBAC (role-based access control)

Crie o arquivo rbac-config.yaml com o seguinte conteúdo abaixo e salve no diretório criado anteriormente.

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: tiller
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: tiller
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
  - kind: ServiceAccount
    name: tiller
    namespace: kube-system
```

### Criação do usuário tiller e cluster role

Se certifique que eestá acessando o diretório C:\Minikube ou ~\Minikube e execute o comando abaixo:

```sh
kubectl create -f rbac-config.yaml
```

### Inicialização do helm

Para inicializalção do helm execute o comando abaixo

```sh
helm init --upgrade --service-account tiller
```

### [Próximo -> Instalação do Qlik Sense Enterprise for Kubernetes](INSTALL.md)

### [Tabela de conteúdo](README.md)