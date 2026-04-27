# 02 - Configurações Pós-Instalação e Hardening

Este documento detalha os ajustes finos realizados no Ubuntu Server 26.04 após a instalação base. O foco aqui foi estabilizar os serviços críticos e garantir a conectividade necessária para o ambiente Docker.

## 1. Atualização e Suporte de Segurança
A primeira ação foi elevar o nível de segurança do sistema através de atualizações e ativação de serviços oficiais.
* **Update & Upgrade:** Sincronização completa dos repositórios.
* **Ubuntu Pro:** Ativação do suporte ESM e Livepatch para correções de kernel sem reboot.

<img width="790" height="191" alt="image" src="https://github.com/user-attachments/assets/1c3ca17f-d373-40e1-b58a-b644067ff06b" /> 

---

## 2. Ajuste Crítico: Inicialização do SSH (Race Condition)
Identifiquei uma falha onde o serviço SSH tentava iniciar antes da interface de rede física, causando erro de *bind*.
* **Causa:** Conflito de tempo entre Kernel e Hardware Real (i7 680).
* **Solução:** Alterado `ListenAddress` no `/etc/ssh/sshd_config` de um IP fixo para `0.0.0.0`.
* **Resultado:** O serviço agora aguarda a disponibilidade de qualquer interface para subir, garantindo acesso imediato pós-boot.

<img width="669" height="277" alt="image" src="https://github.com/user-attachments/assets/2206a1aa-7b6a-487f-8e83-f551446bb1aa" />


---

## 3. Configuração de Rede e DNS Local
Após o fechamento do firewall, a resolução de nomes foi interrompida. Corrigimos isso garantindo que o sistema possa consultar os resolvedores locais e externos.
* **Loopback:** Liberado tráfego na interface `lo` para o `systemd-resolved`.
* **DNS Estático:** Configuração do `/etc/resolv.conf` apontando para o Gateway local e DNS público.

---

## 4. Otimização de Armazenamento e Swap
Preparação do hardware para a carga de trabalho de containers.
* **SSD (500GB):** Configurado arquivo de SWAP para auxiliar os 16GB de RAM.
* **HDD (1TB):** Preparado para montagem como volume de dados do Docker.

<img width="674" height="63" alt="image" src="https://github.com/user-attachments/assets/bdf4da9a-66a7-4b02-8327-63a435fcfab7" />


---

## 5. Validação de Conectividade Externa
Teste final para garantir que o Hardening não quebrou o acesso a serviços essenciais (como o Docker Hub).
<img width="1065" height="178" alt="image" src="https://github.com/user-attachments/assets/839d021c-e731-4b6c-b063-2a76f4385556" />


> **📸 Sugestão de Print:** O resultado do traceroute mostrando o primeiro salto no seu roteador local e a chegada ao destino final, provando que o DNS está resolvendo corretamente.

---
**Status das Configurações:** Finalizado e Validado ✅
