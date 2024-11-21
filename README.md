LINK VIDEO DE FUNCIONAMENTO --> 

# Criação de Ambiente de Desenvolvimento na Azure VM

Este projeto documenta a criação de uma máquina virtual (VM) no Azure, configurada como um ambiente de desenvolvimento para aplicações Android utilizando Android Studio. Abaixo, detalhamos todo o processo para a criação e configuração da VM, incluindo redes, segurança e ferramentas de desenvolvimento instaladas.

## Visão Geral

A VM foi criada no Azure com sistema operacional Linux (Ubuntu 20.04 LTS). O ambiente foi configurado para suportar o desenvolvimento de aplicações Android, com as seguintes etapas principais:

Criação de Resource Group, Virtual Network (VNet) e Network Security Group (NSG).

Criação de uma VM com boas práticas de segurança.

Instalação das ferramentas de desenvolvimento necessárias, incluindo Android Studio, VS Code e Oracle Client.

Configuração de acesso ao banco de dados Oracle.

## Passos Realizados

1. Criação do Resource Group, Virtual Network e Network Security Group

Resource Group: Criado um Resource Group denominado dev-android-rg na região East US para agrupar todos os recursos relacionados ao projeto.

Virtual Network (VNet): Criada a VNet dev-android-vnet com um endereço IP 10.0.0.0/16 e uma sub-rede 10.0.1.0/24.

Network Security Group (NSG): Criado o NSG dev-android-nsg com regras de segurança para permitir o acesso via SSH (porta 22), RDP (porta 3389) e ao banco de dados Oracle (porta 1521).

2. Criação da Máquina Virtual

Sistema Operacional: Escolhido o Ubuntu 20.04 LTS para a VM, denominada dev-android-vm.

Autenticação: Configurada a autenticação por chave SSH gerada localmente para uma conexão segura.

Rede: A VM foi associada à VNet dev-android-vnet e ao NSG dev-android-nsg, garantindo acesso seguro.

3. Configuração do Ambiente de Desenvolvimento

Conexão à VM: Conexão via SSH à VM utilizando a chave gerada.

Atualização do Sistema: Atualização dos pacotes do sistema utilizando os comandos sudo apt update && sudo apt upgrade -y.

Instalação das Ferramentas:

Android Studio: Instalado utilizando o comando sudo snap install android-studio --classic.

VS Code: Instalado utilizando o comando sudo snap install code --classic.

Eclipse (opcional): Instalado utilizando o comando sudo snap install eclipse --classic.

Justificativa para as Ferramentas:

Android Studio é a IDE oficial do Google para desenvolvimento Android, essencial para o desenvolvimento nativo.

VS Code é um editor de código leve e poderoso, com suporte a múltiplas linguagens e boa extensibilidade.

Eclipse é recomendado para desenvolvimento Java, caso seja necessário suporte adicional.

Instalação do Oracle Client: Instalado para permitir o acesso ao banco de dados Oracle, utilizando o comando wget para download e extração do pacote.

4. Configuração do Banco de Dados Oracle

Justificativa para o Oracle Database: O Oracle foi escolhido devido à sua escalabilidade, suporte a transações complexas e segurança, sendo ideal para aplicações empresariais que exigem alta disponibilidade e performance.

Acesso ao Banco: Configurado o Oracle Client para conectar ao banco de dados utilizando o IP e porta 1521.

5. Boas Práticas Aplicadas

Monitoramento e Backup: Habilitado o Azure Monitor para monitoramento e criação de alertas, assim como o backup periódico da VM.

Segurança: Uso de Network Security Group para controlar o acesso à VM, permitindo apenas portas essenciais (SSH, RDP e Oracle).

## Conclusão

Este projeto configura um ambiente completo para o desenvolvimento de aplicações Android em uma máquina virtual no Azure, seguindo boas práticas de segurança e justificativas objetivas para a escolha das ferramentas utilizadas. As etapas acima fornecem uma visão clara de como configurar um ambiente seguro, escalável e eficiente para desenvolvimento.

## Como Reproduzir

Para reproduzir este ambiente, siga os passos descritos acima, garantindo que você tenha uma conta ativa no Azure e permissões adequadas para criar recursos como Resource Groups, VNets e VMs. Além disso, é necessário um cliente SSH para conectar-se à VM e realizar a configuração das ferramentas.

Referências

Documentação do Azure Virtual Machines

Documentação do Android Studio

Documentação do Oracle Database
