---
icon: lucide/brick-wall-fire
---

# Firewall

(Foco em `iptables`)
O firewall é o componente de segurança responsável por monitorar e controlar o tráfego de rede de entrada e saída com base em regras de segurança predefinidas. Ele atua como uma barreira entre uma rede interna confiável e redes externas.

No ambiente Linux (como Debian e Ubuntu), o **`iptables`** é a ferramenta padrão de linha de comando utilizada para configurar o filtro de pacotes do kernel (Netfilter). Em um **Projeto Integrador** que envolve infraestrutura crítica de comunicação — integrando servidores VoIP (como Issabel), automações com IA (Ollama) e serviços de mensageria (WhatsApp) —, o `iptables` é o que garante que a comunicação flua com segurança. Ele impede ataques comuns, como varreduras de portas ou ataques de força bruta, restringindo quem pode se comunicar com as portas sensíveis do servidor.

O `iptables` organiza suas regras em **Tabelas** (sendo a `filter` a principal), **Cadeias** (*Chains*) e **Regras**:
* **INPUT:** Filtra pacotes destinados ao próprio servidor (ex: permitir tráfego SIP na porta UDP 5060 apenas para ramais autorizados, ou acesso SSH na porta 22 apenas para IPs da gerência).
* **OUTPUT:** Filtra pacotes gerados pelo próprio servidor em direção à rede externa.
* **FORWARD:** Filtra pacotes que estão apenas passando pelo servidor (quando ele atua como roteador).
* **Ações Comuns (Targets):**
    * `ACCEPT`: Permite a passagem do pacote.
    * `DROP`: Descarta o pacote silenciosamente (excelente para tráfego malicioso, pois não dá retorno ao atacante).
    * `REJECT`: Recusa o pacote e envia uma mensagem de erro ao remetente.

