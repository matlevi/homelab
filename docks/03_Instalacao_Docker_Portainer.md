# 03 - Instalação do Docker e Portainer

Este documento simplifica a implementação da camada de virtualização do servidor **mark01**, utilizando o **Docker Engine** para execução de containers e o **Portainer CE** como interface de gerenciamento.

## 🏗️ Camada de Virtualização

A escolha do Docker como motor de containers visa garantir o isolamento dos serviços e a facilidade de implantação da stack de monitoramento (Zabbix e Grafana) no hardware (i7 680).

### Componentes Instalados:
*   **Docker Engine:** Runtime principal para o gerenciamento de containers [3].
*   **Portainer CE:** Interface web utilizada para administrar stacks, containers, imagens e volumes de forma visual.

---

## 🛡️ Segurança e Rede (UFW Hardening)

*   **Acesso Administrativo (Portainer):** 
    *   Foi realizada a liberação manual da **porta 9000** no firewall UFW para permitir o acesso à interface web do Portainer via sub-rede local.
    *   <img width="985" height="15" alt="image" src="https://github.com/user-attachments/assets/19f38e61-29aa-448c-98db-8a030c2b83b2" />


---

## 🛠️ Procedimento Realizado

1.  **Instalação do Docker Engine:** Realizada no Ubuntu 26.04 LTS com suporte **Ubuntu Pro** ativo para garantir patches de segurança no runtime.
2.  **Deploy do Portainer:** Container inicializado para facilitar a gestão dos próximos serviços da stack de monitoramento.
3.  **Configuração de Firewall:** Execução do comando `sudo ufw allow 9000/tcp` para habilitar a interface de gestão.

---

**Status da Camada:** Instalada, Monitorada e Protegida ✅
