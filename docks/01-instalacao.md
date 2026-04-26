# 01 - Instalação do Sistema Operacional

Este documento detalha o processo de instalação do sistema base para o servidor **mark01**. A escolha da versão e o método de instalação visam garantir estabilidade e suporte a longo prazo.

## 💾 Preparação do Meio de Instalação
* **ISO:** Ubuntu Server 26.04 LTS.
* **Método:** Criação de pendrive bootável via UEFI.
* **Hardware Alvo:** Máquina real (Intel i7 680, 16GB RAM).

## 🛠️ Processo de Instalação
A instalação foi realizada de forma limpa, eliminando partições pré-existentes de sistemas operacionais anteriores.

### 1. Particionamento de Disco
Para otimizar a performance e a durabilidade, o esquema de armazenamento foi definido da seguinte forma:
* **SSD (500GB):** Destinado ao sistema operacional (`/`), partição de boot e arquivos de sistema. O objetivo é garantir um boot rápido e baixa latência na execução de binários.
* **HDD (1TB):** Reservado para banco de dados.

### 2. Configurações de Rede (Netplan)
Durante a instalação, foi definido um IP estático para evitar conflitos de DHCP e garantir que o acesso via SSH e Portainer seja sempre previsível.
* **IP:** 
* **Gateway:** 
* **DNS:** Configurado inicialmente para `8.8.8.8` 

### 3. Perfil de Usuário
* **Hostname:** `mark01`
* **Usuário:** ***

---

## ✅ Instalação Concluída
A instalação foi finalizada com sucesso, seguida pela atualização imediata dos pacotes (`sudo apt update && sudo apt upgrade`) e ativação do **Ubuntu Pro** para garantir patches de segurança em tempo real.

<img width="496" height="131" alt="primeiro" src="https://github.com/user-attachments/assets/de719b91-321a-4343-a7a9-6c70383f180e" />
