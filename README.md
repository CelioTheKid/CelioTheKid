# Relatório de Diagnóstico e Estabilização de Rede Local (WLAN/LAN)

## 1. Cenário e Problema Identificado
* **Sintoma Inicial:** Colapso intermitente da rede e perda total de pacotes (100% packet loss) para o gateway via Wi-Fi.
* **Sintoma Secundário:** Latência local elevada (ping > 5 ms para o gateway colado na ONT/AP Wi-Fi 6).
* **Equipamentos Envolvidos:** ONT Huawei Wi-Fi 6 (10.0.0.1 / 192.168.1.1), Projetor Smart com EShare/AirPlay (192.168.1.201), hosts Windows e dispositivos móveis.

---

## 2. Diagnóstico por Captura de Pacotes (PCAP Analysis)

### Causa 1: Esgotamento de Airtime por Tempestade de Multicast/Broadcast (L2)
* O projetor e dispositivos locais emitiam fluxos ininterruptos de:
  * **mDNS / Bonjour (224.0.0.251:5353):** Anúncios de `_airplay._tcp.local`, `_raop._tcp.local` e `_companion-link._tcp.local`.
  * **SSDP / UPnP (239.255.255.250:1900):** Notificações contínuas de serviços de renderização de mídia do EShare (`MediaRenderer:1`, `AVTransport:1`).
* **Impacto no Wi-Fi:** No padrão 802.11, pacotes Multicast/Broadcast são transmitidos nas menores taxas básicas legadas (1 Mbps a 6 Mbps) sem confirmação (ACK), consumindo o tempo de transmissão (*airtime*) do canal e causando *queue drop* nos pacotes unicast (ICMP/TCP).

### Causa 2: Saturação de Conexões (NAT/UPnP)
* O protocolo UPnP ativo na ONT permitia o mapeamento descontrolado de portas por hosts locais, inflando a tabela `conntrack` do kernel e degradando o processamento do roteador.

### Causa 3: Sobrecarga de Processamento Local (CPU da ONT)
* Concorrência entre processamento de modulação PON, rádio 802.11ax, criptografia WPA3/WPA2 e *polling* HTTP contínuo da interface Web (`wanStateMonitor.asp` / `refreshTime.asp`).

---

## 3. Ações Executadas e Mitigações Aplicadas

1. **Desativação do UPnP:** Redução do consumo de tabela NAT e eliminação de conexões espúrias na ONT.
2. **Isolamento de Tráfego de Mídia:** Recomendação de migração do projetor para conexão via cabo Ethernet ou fixação exclusiva na frequência de 5 GHz.
3. **Substituição do Hardware:** Troca da ONT pela unidade Wi-Fi 6 AX3000 para suporte a modulações mais altas e múltiplos fluxos espaciais.

---

## 4. Parâmetros de Ajuste Fino Recomendados (WLAN Tuning)

| Parâmetro | Configuração Recomendada | Objetivo |
| :--- | :--- | :--- |
| **Band Steering** | Desativado (SSIDs 2.4G e 5G separados) | Evitar quedas de clientes em transição de banda. |
| **Basic Rates (Taxa Mínima)** | Desmarcar 1, 2, 5.5 e 6 Mbps; fixar $\ge$ 12 Mbps | Acelerar o envio de quadros de gerência/multicast. |
| **IGMP Snooping / M2U** | Ativado (Multicast to Unicast) | Converter mDNS/SSDP em unicast de alta modulação. |
| **Largura de Canal 5 GHz** | 80 MHz (Canais baixos: 36 a 48) | Maximizar throughput e evitar eventos DFS. |
| **DTIM Period** | 2 ou 3 | Otimizar economia de energia e tráfego de beacon. |

---

## 5. Arquitetura Definitiva (Topologia de Alto Desempenho)
Para ambientes com múltiplos dispositivos de streaming, telemetria e trabalho contínuo:
* **ONT em modo Bridge:** Responsável unicamente pela conversão óptico-elétrica e autenticação GPON.
* **Roteador / AP Dedicado:** Hardware dedicado para gerenciar NAT, DHCP, QoS e rádio Wi-Fi com CPU independente.
