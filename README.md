# 🚀 Real Homelab Server - Project Mark01

Este repositório documenta a montagem, configuração e administração de um servidor **Homelab físico**, focado em virtualização com **Docker** e segurança rigorosa (Hardening). 

Diferente de laboratórios virtuais, este projeto é executado em hardware dedicado, enfrentando desafios reais de redes físicas, latência e persistência de dados em uma máquina real.

---

## 💻 Hardware (Camada 1 - Física)

O servidor foi construído para máxima eficiência dentro da arquitetura disponível, garantindo que "tudo o que for feito é real".

* **Hostname:** `mark01`
* **CPU:** Intel Core i7 680 (Arquitetura Lynnfield)
* **Memória:** 16GB RAM DDR3
* **Armazenamento OS:** SSD 500GB 
* **Armazenamento Dados:** HDD 1TB 
* **Rede:** Gigabit Ethernet (Interface física operando em 1000Mb/s)

---

## 🛡️ Stack de Software & Segurança

A filosofia do projeto é **"Zero Trust"**. O servidor opera sob uma política de privilégio mínimo, protegendo os serviços de containers e o acesso administrativo.

* **Sistema Operacional:** Ubuntu Server Ubuntu 26.04 LTS (Resolute Raccoon)
* **Segurança de Pacotes:** Ubuntu Pro (ESM-Apps & Livepatch habilitados)
* **Firewall (UFW):** Política restritiva de entrada e saída (**Deny All** Inbound/Outbound)
* **Containers:** Docker Engine + Portainer CE 

### Estratégia de Rede (UFW Hardening)
O tráfego é monitorado e limitado para prevenir vetores de ataque comuns:
* **Entrada:** SSH limitado à sub-rede local com regra de `limit` contra Brute Force.
* **Saída:** Bloqueio total por padrão. Portas 53 (DNS) e 443 (HTTPS) são liberadas manualmente apenas para manutenção e `docker pull`.

---

## 📂 Estrutura do Repositório

```text
homelab/
├── README.md
├── 01_Instalacao_Bare_Metal.md
├── 02_Configuracao_Rede_Netplan.md
├── 03_Instalacao_Docker_Portainer.md
├── 04_Monitoramento_Zabbix_Grafana.md       

