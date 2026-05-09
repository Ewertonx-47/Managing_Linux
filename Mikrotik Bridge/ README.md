Laboratório: Migrando Proxmox da rede do roteador para rede Mikrotik 

Nesse laborátorio será feito a migração do servidor Proxmox, que estava na rede do roteador doméstico, para a rede do Mikrotik. Resumo geral da rede doméstica:

Rede: 192.168.1.0
Gateway: 192.168.1.1
Mask: 255.255.255.0
Broadcast: 192.168.1.255

O Mikrotik está recebendo internet do roteador doméstico, porém foi criado outra rede a partir da ether2 em diante do equipamento. No mikrotik, as interfaces são independentes, diferente de um roteador fornecido por um provedor em varejo, nesse caso as portas do equipamento já são entregas com uma configuração de bridge interna. 

No Mikrotik, a ether1 é um DHCP client para receber IP do modem:

(imagem)

-
