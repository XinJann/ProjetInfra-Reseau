# **Utilisation**

1. Faire glisser un VPCS dans notre infra, puis le brancher sur n'importe quel Switch "Access" (exepté le 5) sur une des interfaces suivantes :  
   - 0/0
   - 0/1
   - 0/2

2. Une fois branché, allumez le VPCS et accédez à sa Console, taper la commande :  
   - ip dhcp  

### Il est maintenant possible de ping n'importe quel appareil du LAN, de ping des IP publics et surtout de pouvoir ping le futur server Web "web.projetinfra.net"  

<br>

### Remarque : Il est possible de voir le fonctionnement du protocol NAT.
 - Ouvrez la console du router et taper la commande **debug ip nat**  
