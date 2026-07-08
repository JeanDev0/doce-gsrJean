---
icon: lucide/globe-lock
---

# VPN 

A VPN estabelece uma conexão protegida (um túnel criptografado) entre um dispositivo e uma rede privada, utilizando a infraestrutura da internet pública. 

Com a implementação do **WireGuard**, utiliza-se um dos protocolos de VPN mais modernos, enxutos e de alta performance disponíveis atualmente. Diferente de soluções tradicionais (como OpenVPN ou IPsec), o WireGuard opera diretamente no *kernel* do Linux e utiliza criptografia de estado da arte (*state-of-the-art*). Sua autenticação é feita através da troca de chaves públicas, semelhante ao SSH, gerando uma interface de rede virtual (normalmente `wg0`).
* **Aplicação:** Permite o acesso remoto à infraestrutura de forma extremamente rápida e com baixo consumo de processamento. O tráfego encapsulado garante que painéis administrativos, servidores e recursos locais sejam acessados com segurança total e latência mínima, como se o usuário estivesse fisicamente conectado à rede interna.
