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
