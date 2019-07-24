# **Qlik Sense Enterprise for Kubernetes em Minikube** (Ambiente de Teste)

## Pós instalação

### Verifique o status dos pods

Aguarde a execução de todos pods, este processo poderá demorar alguns minutos, porém é possível acompanhar utilizando o comando abaixo

```sh
kubectl get pods
```

O retorno será algo como:

```sh
NAME                                                  READY   STATUS              RESTARTS   AGE
qliksense-audit-5f9dcdfb7c-459x5                      1/1     Running             0          51m
qliksense-chronos-ff5cc9dbd-kj6xs                     2/2     Running             0          51m
qliksense-chronos-worker-658c9cdccd-wgtw4             1/1     Running             0          51m
qliksense-collections-566fbf4f5f-h9v7w                1/1     Running             0          51m
qliksense-data-connector-odbc-cmd-85bd5bfc4c-wlbpf    1/1     Running             0          51m
qliksense-data-connector-odbc-rld-5585dd56cc-f958k    1/1     Running             0          51m
qliksense-data-connector-qwc-cmd-bccb98b56-2rzm6      1/1     Running             0          51m
qliksense-data-connector-qwc-rld-59d998dd66-j5ktw     1/1     Running             0          51m
qliksense-data-connector-rest-cmd-565b995965-9rcck    1/1     Running             0          51m
qliksense-data-connector-rest-rld-69b8c4cb5-h7hfd     1/1     Running             0          51m
qliksense-data-prep-6557d7d79d-cttv6                  1/1     Running             0          51m
qliksense-data-rest-source-697ffcdfc8-lwvhh           1/1     Running             0          51m
```

### Debug de um pod

Para realizar o debug de um pod utilize:

```sh
kubectl logs nome-do-pod

kubectl describe pod nome-do-pod
```

### Atualização do Qlik Sense ou YAML

Caso queira atualizar o Qlik Sense ou tenha alterado algum valor no arquivo values.yaml posteriormente ao seu deploy inicial você pode rodar o seguinte comando:

```sh
helm upgrade qliksense qlik/qliksense -f values.yaml
```

### [Próximo -> Acessando o Qlik Sense Enterprise for Kubernetes](ACCESS.md)

### [Voltar <- Instalação do Qlik Sense Enterprise for Kubernetes](INSTALL.md)

### [Tabela de conteúdo](README.md)