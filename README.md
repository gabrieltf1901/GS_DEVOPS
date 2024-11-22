NOME: GABRIEL TORRES FERNANDES  
RM: 553635


LINK VIDEO DE FUNCIONAMENTO --> https://youtu.be/wOEnaiKIJKM


# Ambiente de Desenvolvimento com VMs no Azure

Este repositório documenta o processo de configuração e execução de duas VMs (Backend e Frontend) no Microsoft Azure. As VMs são configuradas para desenvolver, testar e executar aplicações Java e Android com suporte ao Oracle Database.

## 1. Descrição Geral

### VM Backend
- Sistema Operacional: Windows Server 2022
- Aplicação: Projeto Java
- Banco de Dados: Oracle Database
- Ferramentas Instaldas:
    - JDK 17
    - IntelliJ IDEA Community Edition

### VM Frontend
- Sistema Operacional: Ubuntu 20.04 (Linux)
- Aplicação: Projeto Android
- Banco de Dados: Oracle Database
- Ferramentas Instaladas:
    - OpenJDK 17
    - Android Studio

## 2. Configuração das VMs

### 2.1. Requisitos
- Conta no Azure Portal.
- Cliente SSH instalado (para Linux).
- Cliente Remote Desktop (RDP) instalado (para Windows).

### 2.2. Recursos Criados no Azure
- Os seguintes recursos são compartilhados entre as VMs:
- Resource Group
- Virtual Network (VNet) com Subnets dedicadas.
- Network Security Group (NSG) com regras para portas:
    - SSH (22)
    - RDP (3389)
    - Banco de Dados Oracle (1521)

## 3. Instruções para Rodar as VMs
   
### 3.1. VM Backend (Windows Server)

1. Acesse o Azure Portal:
    - Navegue até a VM chamada VM-Desenvolvimento.
    - Anote o Endereço IP Público.
2. Conecte-se via RDP:
    - Abra o cliente RDP no Windows (mstsc).
    - Insira o IP público da VM como o Host.
    - Use as credenciais criadas durante a configuração:
        - Usuário: adminuser
        - Senha: Configurada no Azure.
3. Configuração na VM:
     - Instale as ferramentas necessárias, como JDK e IntelliJ IDEA.
    -  Faça o deploy do projeto Java:
        -  Navegue até o diretório do projeto.
        - Compile e execute o projeto:

java -jar <seu-projeto>.jar

- Verifique o banco de dados Oracle usando o application.properties no projeto.

4. Testar a Aplicação:

Acesse a aplicação via navegador:

http://<IP_PÚBLICO_DA_VM>:8080


3.2. VM Frontend (Linux - Ubuntu)
  1. Acesse o Azure Portal:
    - Navegue até a VM chamada VM-Frontend.
    - Anote o Endereço IP Público.
  2. Conecte-se via SSH:

Use o terminal para se conectar à VM:

ssh adminuser@<IP_PÚBLICO_DA_VM>

- Insira a senha configurada no Azure.
  
  3. Configuração na VM:

    - Atualize o sistema e instale o Android Studio:

sudo apt update && sudo apt upgrade -y
wget <URL_ANDROID_STUDIO>
tar -xvzf android-studio.tar.gz
sudo mv android-studio /opt/
echo 'export PATH=$PATH:/opt/android-studio/bin' >> ~/.bashrc
source ~/.bashrc

- Execute o Android Studio:

studio.sh

Desenvolvimento e Testes:

  - Abra o projeto Android e conecte-o ao backend via API.
  - Configure a conexão ao banco de dados Oracle, se necessário.
    
4. Banco de Dados Oracle
Ambas as VMs estão conectadas ao banco de dados Oracle pela porta 1521.

Configuração do application.properties (Backend e Frontend)

spring.datasource.url=jdbc:oracle:thin:@<IP_PÚBLICO_DA_VM>:1521/ORCL
spring.datasource.username=<USUARIO>
spring.datasource.password=<SENHA>

5. Justificativas
   
  - Azure: Plataforma flexível e segura para ambientes de desenvolvimento.
  - Windows Server e Ubuntu: Atendem aos requisitos de backend e frontend com     estabilidade e ferramentas adequadas.
  - IntelliJ IDEA e Android Studio: Ferramentas líderes de mercado com ampla      documentação e suporte para desenvolvimento.
  - Oracle Database: Solução robusta e confiável para aplicações corporativas     com alto volume de dados.



