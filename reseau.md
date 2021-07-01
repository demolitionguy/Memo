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

