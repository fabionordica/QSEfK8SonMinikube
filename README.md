# **Qlik Sense Enterprise for Kubernetes em Minikube** (Ambiente de Teste)


## YouTube
https://www.youtube.com/watch?v=iCM8QfRXSoE

## Objetivo
Este documento foi criado para auxiliar a criação de um ambiente de teste em Minikube e utilizando o usuário de exemplo _harley@qlik.example_.

Os comandos que foram documentados devem ser interpretados antes de serem executados. 


## Pré-Requisitos

* Conhecimento Linux.

* Conhecimento Kubernetes e helm.

* Requisitos de sistema conforme https://help.qlik.com/en-US/sense/June2019/Subsystems/PlanningQlikSenseDeployments/Content/Sense_Deployment/Introduction/system-requirements.htm



## Preparando seu ambiente

* Instale o VirtualBox 6 (https://www.virtualbox.org/wiki/Downloads)

* Instale o Chocolatey (https://chocolatey.org/install).

* Instale o Kubernetes CLI utilizando o Chocolatey (https://chocolatey.org/packages/kubernetes-cli).

* Instale o Minikube utilizando o Chocolatey (https://chocolatey.org/packages/Minikube)

* Instale o helm 2.13.0 utilizando o Chocolatey (https://chocolatey.org/packages/kubernetes-helm/2.13.0).

## Conteúdo

* [Provisionando o ambiente](PROVISIONING.md)
* [Instalação do Qlik Sense Enterprise for Kubernetes](INSTALL.md)
* [Pós instalação](PINSTALL.md)
* [Acessando o Qlik Sense Enterprise for Kubernetes](ACCESS.md)
* [Parando ou deletando o Minikube](STOP_DELETE.md)
