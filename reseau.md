# Vlan

Switch: redirige les trames en fonction de l'adresse mac (donc il y a des tables).  
En fonction de l'adresse mac source. Table: @mac <-> port  
Adresse inconnue -> broadcast: transmis à tout le monde (logique).  

VLan : virtual local area network. Réseau local virtuel.

Lan: tout le monde peut communiquer avec tout le monde sans passer par un routeur (même domaine de broadcast).

Vlan1 est créé par défaut. Tous les ports du switch appartiennent à ce Vlan.  
Vlan: 1 domaine de broadcast.  
1 Vlan <-> 1 sous-réseau IP dédié. Les pc des Vlan doivent être dans le même plan d'adressage IP!  
PVID: Port Vlan IDentifier.  
PVID d'un port du switch: numéro (identifiant) Vlan qui sera associé à toute trame entrante sur le switch par ce port.

# Masques de sous-réseau

11111111.11111111.11111111.00000000  
\<----------réseau------------\>\<machine\>
  
Masque en décimal: 255.255.255.0  
  
192.168.25.0 réservé pour le réseau  
192.168.25.255 réservé pour le broadcast  
Il reste 254 possibilités pour les machines.  
  
Exemple:  
Masque: 255.255.255.248 (248 = 11111 000 , les 11111 sont pour la partie réseau)  
Réseau 192.168.25.32 avec ce masque
  
# Sous-réseau

X.O réseau  
X.1  
X.254  
X.255 broadcast
	
Si masque avec des bits non contigus les machines auraient des numéros qui ne se suivraient pas.
	
Masque -> nombre de machines dans le réseau  
Réseau -> adresse de départ
	
Pour trouver toutes les adresses réseau disponibles  
Exemple:   
on veut 50 machines -> masque: 255.255.255.192 (192 = 11 000 000)  
256-192=64 machines (50 n'est pas possible donc on prend 64).
	
L'adresse du réseau doit être un multiple de 64. Adresses de réseau possibles:  
10.0.0.0  
10.0.0.64  
10.0.0.128  
10.0.0.192  
	
Prenons le réseau 10.0.0.16  
Donc 10.0.0. 0001 000 (réseau) avec le masque 1100 0000  
Donc la machine 0001 0001 serait dans le réseau  
Mais la machine max serait 0011 1111. On n'aurait plus 64 possibilités.
	
On veut une plage de 69.0.0.0 à 79.255.255.255. Quel masque et quel réseau utiliser? Il faut découper en plusieurs sous-réseaux. On peut faire:  
69.0.0.0 avec le masque 255.0.0.0  
Puis 70.0.0.0 avec le masque 255.0.0.0  
71.0.0.0 avec le masque 255.0.0.0  
Mais ça fait 11 sous-réseaux; c'est pas optimal.
	
128|64|32|16|8|4|2|1  
2^7|2^6|2^5|2^4|2^3|2^2|2^1|2^0  
	
De 69 à 79 il y a 11. 11 n'est pas possible (ce n'est pas une puissance de 2). On peut avoir 16 ou 8. 16 est trop donc on prend 8 et on complétera. On décrira donc 8 valeurs.  
69: 01 000 101  
79: 01 100 100  
Dans cette plage toutes les machines ont le 2d bit à 1 (en partant de la gauche): 64. 64 +8 =72  
	
01 00 1000 : le 1er 1 est 64; le 2d 1 est 8. Les trois derniers zéros laissent 8 possibilités d'adresses pour des machines.  
On a donc de 01 00 1000 (réseau 72, masque 248.0.0.0: 111 11000) jusqu'à 01 100 100 (79)  
	
Réseau -> adresse de départ  
Nombre de machines -> masque (indique la fin)  
	
Adresses privées:  
10.0.0.0 /255.0.0.0  
192.168.0.0 /255.255.0.0  
172.16.0.0 /255.240.0.0 (240 = 1111 0000)
	
La machine appartient elle au réseau? ET logique entre adresse et masque  
Exemple:  
192.168.0.140  masque: 255.255.255.128  
Machine A 192.168.0.20  
Machine B 192.168.0.185   
Les machines A et B sont-elles sur le même réseau?  

192.168.0.140  
ET 255.255.255.128    
= 192.168.0.128  

140: 1 000 11 00    
ET 128: 1 000 00 00    
= 1 000 00 00  

192.168.0.185    
ET 255.255.255.128    
= 192.168.0.128  

185: 10 111 001    
ET     10 000 000    
= 10 000 000  

192.168.0.20    
ET 255.255.255.128    
= 192.168.0.0  

20: 0001 0100    
ET 1000 0000    
= 0000 0000    
	
# Tunnels SSH

`ssh -N -f -L 3128:proxy.bidule.fr:3128 nom_login@machine.bidule.fr`  
`ssh -N -f -L port de mon poste:machine cible:port par lequel tout arrive sur proxy.bidule.fr intermédiaire`

Tunnel depuis mon poste vers la machine **machine.bidule.fr** en ouvrant le port 3128 sur mon poste.  
Tout ce qui entre par ce port est redirigé via **machine.bidule.fr** vers le port 3128 du **proxy.bidule.fr**.

Port < 1024: réservés pour le système.

.ssh/config 
    Host machine  
      Hostname machine.bidule.fr  
      LocalForward 3128 proxy.bidule.fr:3128  
      LocalForward 1025 smtp-p.bidule.fr:25  
et on fait `ssh machine` au lieu de 2 tunnels: `ssh -N -f -L 1025:smtp-p.bidule.fr:25 -L 3128:proxy.bidule.fr:3128 nom_login@machine.bidule.fr`

Tunnel = port forwarding.

