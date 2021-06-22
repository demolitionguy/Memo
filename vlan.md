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
