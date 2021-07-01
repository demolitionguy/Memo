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
  
