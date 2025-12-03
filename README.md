# Projeto 01 - DevOps com Vagrant e Ansible

## 📌 Sobre o Projeto

Este repositório contém a infraestrutura como código (IaC) desenvolvida para o **Projeto 01** da disciplina de **Administração de Sistemas Abertos** (2025.2), ministrada pelo Prof. Leonidas Lima no **IFPB - Campus João Pessoa**.

O objetivo é provisionar um ambiente virtual automatizado e configurar serviços essenciais utilizando **Vagrant** e **Ansible**.

## 🏗️ Arquitetura do Ambiente

O projeto utiliza 4 máquinas virtuais baseadas em **Debian 12 (Bookworm)** com o provider **VirtualBox**:

* **arq (Servidor de Arquivos):** DHCP, DNS, LVM e compartilhamento NFS
* **db (Banco de Dados):** MariaDB configurado e acessível na rede interna
* **app (Aplicação):** Servidor web Apache com página personalizada
* **cli (Cliente):** Estação de testes com Firefox e suporte a X11 forwarding

## 🛠️ Tecnologias Utilizadas

* Vagrant
* VirtualBox
* Ansible
* Linux (Debian)
* Shell Script

## 📋 Pré-requisitos

Certifique-se de ter instalado:

* VirtualBox
* Vagrant
* Ansible

## 🚀 Como Executar

1. Clone este repositório:

   ```bash
   git clone <url-do-seu-repositorio>
   cd <nome-do-repositorio>
   ```

2. Inicialize o ambiente:

   ```bash
   vagrant up
   ```

3. O provisionamento das máquinas será realizado automaticamente pelos playbooks do Ansible.

👥 Integrantes da Equipe

Victor Henrique Santos Ferreira

Tyrone Michel Caldas Albuquerque

---

*Projeto desenvolvido para fins educacionais no Instituto Federal da Paraíba (IFPB).*
