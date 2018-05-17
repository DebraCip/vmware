---
copyright:
  years: 1994, 2017
lastupdated: "2017-06-12"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Visão geral do VMware vSphere 6 NSX

O VMware NSX&reg; é uma plataforma de virtualização de segurança e rede de software que fornece o modelo operacional de uma máquina virtual para a rede. As redes virtuais reproduzem o modelo de rede Layer2 - Layer7 em software, permitindo que topologias de rede multicamada complexas sejam criadas e provisionadas programaticamente em segundos, sem a necessidade de Redes Privadas do {{site.data.keyword.BluSoftlayer_notm}} adicionais. O NSX também fornece um novo modelo para segurança de rede. Os perfis de segurança são distribuídos e aplicados por portas virtuais e se movem com as máquinas virtuais.

O NSX suporta a estratégia de data center definido por software do VMware. Ao estender os recursos de virtualização de abstração, conjunto e automação em todos os recursos e serviços do data center, a arquitetura do data center definido por software simplifica e acelera o fornecimento e o gerenciamento de recursos de computação, armazenamento e rede por meio da automação orientada a política. Ao virtualizar a rede, o NSX oferece um novo modelo operacional para rede que quebra as barreiras atuais da rede física e permite que o VMware e o {{site.data.keyword.BluSoftlayer_notm}} obtenham melhor velocidade e agilidade com custos reduzidos.

O NSX inclui uma biblioteca de serviços de rede lógica - comutadores lógicos, roteadores lógicos, firewalls lógicos, balanceadores de carga lógicos, VPN lógica e segurança distribuída. É possível criar combinações customizadas desses serviços em redes virtuais baseadas em software isoladas que suportam aplicativos existentes sem modificação ou entregam requisitos exclusivos para novas cargas de trabalho do aplicativo. As redes virtuais são provisionadas e gerenciadas programaticamente independentemente das construções de rede do {{site.data.keyword.BluSoftlayer_notm}}. Essa desvinculação de hardware apresenta agilidade, velocidade e eficiência operacional que podem transformar as operações do data center. Os benefícios do NSX incluem os recursos a seguir:
* Automação do data center
* Serviços de rede de autoatendimento
* Rápida implementação do aplicativo com fornecimento automatizado de rede e serviço
* Isolamento de ambientes de desenvolvimento, teste e produção na mesma infraestrutura bare metal
* Nuvens de diversos locatários de conta única

O NSX pode ser configurado por meio do vSphere Web Client, de uma interface da linha de comandos (CLI) e da API REST. Os principais serviços de rede oferecidos pelo NSX são:

## Comutadores lógicos
Uma implementação na nuvem ou um data center virtual pode ter uma variedade de aplicativos em múltiplos locatários. Esses aplicativos e locatários requerem isolamento entre si para segurança, isolamento de falha e para evitar problemas de sobreposição do endereçamento IP. O comutador lógico NSX cria domínios ou segmentos de transmissão lógica (vWires VXLAN) aos quais uma máquina virtual de aplicativo ou locatário pode ser conectada logicamente. Isso permite a flexibilidade e a velocidade de implementação enquanto ainda fornece todas as características de domínios de transmissão de uma rede física (VLANs) sem expansão da Camada 2 física. Comutadores lógicos permitem que milhares de redes de locatário sejam provisionadas em uma única Rede Privada do {{site.data.keyword.BluSoftlayer_notm}} (VLAN). Um comutador lógico é distribuído e pode abranger clusters de cálculo arbitrariamente grandes, mesmo em pods dentro do mesmo data center. Isso permite a mobilidade da máquina virtual dentro do data center sem limitações da Camada 2 física (VLAN) em pods.

## Roteadores lógicos
O roteamento dinâmico fornece as informações de encaminhamento necessárias entre domínios de transmissão da camada 2 (VXLAN vWires/Comutadores Lógicos) permitindo, assim, que você diminua os domínios de transmissão da camada 2 e melhore a eficiência e a escala da rede. O NSX estende essa inteligência para onde as cargas de trabalho residem para fornecer funções de roteamento Leste-Oeste. Isso permite a comunicação mais direta entre máquinas virtuais sem a necessidade onerosa ou oportuna de estender hops. Ao mesmo tempo, o NSX também fornece entrada/saída de conectividade Norte-Sul de data centers do {{site.data.keyword.BluSoftlayer_notm}} permitindo, assim, que locatários acessem redes públicas de forma segura e eficiente.

## Firewall lógico
O firewall lógico fornece mecanismos de segurança para datacenters virtuais dinâmicos. O componente Distributed Firewall de um Firewall Lógico do NSX permite segmentar entidades de datacenter virtual, como máquinas virtuais, com base nos nomes e atributos da VM, na identidade do usuário, em objetos do vCenter como data centers e hosts, bem como atributos de rede tradicional, como endereços IP, VLANs, etc. O componente Edge Firewall ajuda você a satisfazer as necessidades de segurança do perímetro chave, tal como construir DMZs com base em construções de IP/VLAN, isolamento entre locatários em datacenters virtuais com diversos locatários, Conversão de Endereço de Rede (NAT), VPNs e VPNs de SSL baseado em usuário. Os Edge Firewalls podem ser alavancados em combinação com ou no lugar dos serviços Vyatta e Fortinet do {{site.data.keyword.BluSoftlayer_notm}} para proteção do perímetro. O recurso Monitoramento de Fluxo do Firewall exibe a atividade de rede entre máquinas virtuais no nível do protocolo de aplicativo. É possível usar essas informações para auditar o tráfego de rede, definir e refinar as políticas de firewall e identificar ameaças à sua rede.

## Redes privadas virtuais (VPNs) lógicas
O SSL VPN-Plus permite que usuários remotos acessem aplicativos corporativos privados. A VPN do IPSec oferece conectividade site a site entre uma instância do NSX Edge e sites remotos (VMware em execução no {{site.data.keyword.BluSoftlayer_notm}}). As VPNs L2 permitem que você estenda seu data center permitindo que máquinas virtuais mantenham a conectividade de rede entre limites geográficos e entre data centers do {{site.data.keyword.BluSoftlayer_notm}} e seu ambiente VMware local.

## Balanceador de carga lógico
O balanceador de carga NSX Edge permite que o tráfego de rede siga vários caminhos para um destino específico. Ele distribui solicitações de serviço recebidas uniformemente entre vários servidores de tal forma que a distribuição de carga seja transparente para os usuários. O balanceamento de carga, portanto, ajuda a alcançar a utilização de recurso ideal, maximizando o rendimento, minimizando o tempo de resposta e evitando a sobrecarga. O NSX Edge fornece balanceamento de carga até a Camada 7.

## Service Composer
O Service Composer ajuda a provisionar e designar serviços de rede e segurança para aplicativos em uma infraestrutura virtual. Esses serviços podem ser mapeados e aplicados em máquinas virtuais nos grupos de segurança. O Data Security fornece visibilidade para dados sensíveis armazenados em ambientes virtualizados e de nuvem de sua organização, incluindo {{site.data.keyword.BluSoftlayer_notm}}. Com base nas violações relatadas pelo NSX Data Security, é possível assegurar que os dados sensíveis sejam adequadamente protegidos, além de avaliar a conformidade com os regulamentos no mundo inteiro.

## NSX Extensibility
Os parceiros VMware podem integrar suas soluções de serviços de rede com a plataforma NSX, o que permite que os clientes tenham uma experiência integrada em produtos VMware e soluções de parceiros. Os operadores de data centers podem fornecer redes virtuais complexas multicamada em segundos, independente da topologia de rede subjacente ou dos componentes do {{site.data.keyword.BluSoftlayer_notm}}.

## Componentes principais do NSX
Esta seção descreve os componentes principais do NSX que seriam implementados no {{site.data.keyword.BluSoftlayer_notm}}. Esses componentes podem ser configurados/gerenciados por meio do vSphere Web Client, de uma interface da linha de comandos (CLI) e da API REST. O VMware NSX requer um ambiente do {{site.data.keyword.BluSoftlayer_notm}} funcional com pelo menos o vSphere e o vCenter versão 6 implementados. Todos os componentes descritos nesta seção são implementados como VMs do dispositivo VMware em execução no {{site.data.keyword.BluSoftlayer_notm}}. Os componentes NSX não são suportados como Instâncias de Servidor Virtual (VSI). É recomendável que seja seguida a orientação para criar um Cluster de Gerenciamento ESX dedicado, além disso, um Cluster Edge Services também pode ser necessário, conforme será discutido mais adiante nesta publicação.

<!-- ![Figure 1](images/vmware6_nsx_overview_1.png)-->

## NSX Manager
O NSX Manager é o componente de gerenciamento de rede centralizado do NSX e é instalado como um dispositivo virtual em um host ESX em seu ambiente do vCenter Server. A Arquitetura do {{site.data.keyword.BluSoftlayer_notm}} recomenda que essa VM seja implementada em um Cluster ESX de Gerenciamento dedicado. Um NSX Manager é mapeado para um único ambiente do vCenter Server e múltiplas instâncias do NSX Edge, do vShield Endpoint e do NSX Data Security.

## NSX vSwitch
O NSX vSwitch é o software que opera em hosts ESX do {{site.data.keyword.BluSoftlayer_notm}} para formar uma camada de abstração de software entre os servidores e a rede física. À medida que as demandas nos Data Centers continuam a crescer e acelerar, os requisitos relacionados à velocidade e ao acesso aos dados em si continuam crescendo também. Na maioria das infraestruturas, o acesso à máquina virtual e a mobilidade geralmente dependem da infraestrutura de rede física e dos ambientes de rede física nos quais elas residem. Isso pode forçar as cargas de trabalho virtuais em ambientes abaixo do ideal devido aos limites potenciais da camada 2 ou da camada 3, tal como estar conectado a Redes Privadas do {{site.data.keyword.BluSoftlayer_notm}} (VLANs) específicas em pods específicos. O NSX vSwitch permite colocar essas cargas de trabalho virtuais em qualquer infraestrutura disponível no data center, independentemente da infraestrutura de rede física subjacente. Isso não apenas permite maior flexibilidade e mobilidade, mas também maior disponibilidade e resiliência.

## NSX Controller 
O NSX Controller é um sistema de gerenciamento de estado distribuído avançado que controla redes virtuais e túneis de transporte de sobreposição de VXLAN. O NSX Controller é o ponto de controle central para todos os comutadores lógicos em uma rede e mantém informações sobre todas as máquinas virtuais, hosts, comutadores lógicos e VXLANs. O controlador suporta três modos de plano de controle de comutador lógico: Multicast, Unicast e Híbrido. Esses modos separam o NSX da rede física. O {{site.data.keyword.BluSoftlayer_notm}} requer o modo Unicast pois as Redes Privadas do {{site.data.keyword.BluSoftlayer_notm}} (VLANs) não oferecem serviços IGMP para o modo Multicast ou Híbrido. Os NSX Controllers utilizarão o modo Unicast com terminais de túnel virtuais (VTEPS) para fornecer aprendizado mac e outras funções para permitir Transmissão de VXLAN, Unicast desconhecido e tráfego Multicast (BUM) dentro de um comutador lógico. O modo unicast replica todo o tráfego BUM localmente no host e não requer configuração de rede física fora da conectividade da Camada 3 entre VTEPS. Os NSX Controllers são implementados pelo NSX Manager como um conjunto mínimo de 3 nós do controlador, bem como vários outros nós para suportar os serviços de roteamento da Camada 3 (distribuídos). Todos os nós são implementados como máquinas virtuais e são gerenciados pelo NSX Manager em um Cluster ESX Management em {{site.data.keyword.BluSoftlayer_notm}}.

## NSX Edge
O NSX Edge fornece segurança avançada de rede e serviços de gateway para isolar redes virtualizadas. É possível instalar um Edge NSX como um roteador lógico (distribuído) ou como um gateway de serviços. O roteador lógico (distribuído) do NSX Edge fornece roteamento distribuído Leste-Oeste com espaço de endereço IP de locatário e isolamento de caminho de dados. As máquinas virtuais ou cargas de trabalho que residem no mesmo host em diferentes sub-redes podem se comunicar entre si sem precisar atravessar uma interface de roteamento tradicional. O Gateway do NSX Edge conecta redes stub isoladas a redes compartilhadas (uplink) fornecendo serviços de gateway comuns, como DHCP, VPN, NAT, roteamento dinâmico e balanceamento de carga. As implementações comuns do NSX Edge incluem na DMZ, em Extranets VPN e em ambientes de nuvem de diversos locatários nos quais o NSX Edge cria limites virtuais para cada locatário.