---
icon: lucide/brick-wall-fire
---

# Firewall

O firewall (Foco em `iptables`) é o componente de segurança responsável por monitorar e controlar o tráfego de rede de entrada e saída com base em regras de segurança predefinidas. Ele atua como uma barreira entre uma rede interna confiável e redes externas.

No ambiente Linux (como Debian e Ubuntu), o **`iptables`** é a ferramenta padrão de linha de comando utilizada para configurar o filtro de pacotes do kernel (Netfilter). Na implantação de um sistema sensível como o **PEC e-SUS**, o `iptables` é crucial para proteger os dados do Prontuário Eletrônico. Ele garante que apenas as portas de acesso web (como a 8080, 80 ou 443) fiquem disponíveis para a rede da unidade de saúde, bloqueando estritamente qualquer acesso externo a serviços críticos e portas vulneráveis, como a do banco de dados (ex: porta 5432 do PostgreSQL).

O `iptables` organiza suas regras em **Tabelas** (sendo a `filter` a principal), **Cadeias** (*Chains*) e **Regras**:

* **INPUT:** Filtra pacotes destinados ao próprio servidor (ex: permitir acesso web ao PEC e-SUS apenas para os IPs da rede local da clínica, ou acesso SSH apenas para a rede do suporte técnico).
* **OUTPUT:** Filtra pacotes gerados pelo próprio servidor em direção à rede externa.
* **FORWARD:** Filtra pacotes que estão apenas passando pelo servidor (quando ele atua como roteador).
* **Ações Comuns (Targets):**
    * `ACCEPT`: Permite a passagem do pacote.
    * `DROP`: Descarta o pacote silenciosamente (excelente contra varreduras na rede, pois não dá retorno ao atacante).
    * `REJECT`: Recusa o pacote e envia uma mensagem de erro ao remetente.
