# Exploring Your First Network

Scripts Bash d'observation réseau pour un environnement Linux disposant déjà
de Bash, iproute2, ping et getent. Ils n'installent aucun paquet, ne modifient
aucune configuration et s'exécutent sans privilèges administrateur.

| Script | Fonction |
| --- | --- |
| `list_interfaces.sh` | Tableau bref de toutes les interfaces et de leurs adresses IPv4/IPv6. |
| `show_links.sh` | Tableau bref des états, adresses de liaison et indicateurs des interfaces. |
| `test_loopback.sh` | Découvre la première adresse IPv4 de portée host, retire le préfixe CIDR et envoie quatre requêtes ICMP. |
| `show_default_route.sh` | Toutes les routes IPv4 par défaut, sans filtrage des attributs. |
| `resolve_hostname.sh HOSTNAME` | Résultat intégral de la base système hosts pour l'argument fourni. |
| `show_neighbors.sh` | Table actuelle des voisins IPv4, sans envoyer de trafic. |
| `list_listening_tcp.sh` | Sockets TCP en écoute, adresses et ports numériques, en-tête inclus et sans informations de processus. |

Lancer un script avec `./nom_du_script.sh`. Seul `resolve_hostname.sh` attend
un argument. Les sorties natives sont conservées ; les tables vides de routes
ou de voisins restent des résultats valides. Les valeurs dépendent du système
au moment de l'exécution et ne sont jamais recopiées depuis les exemples.

## Notions à retenir

Une interface relie le système à un réseau ; son adresse de liaison (souvent
MAC) appartient à la couche liaison, tandis que ses adresses IP permettent
l'adressage réseau. La boucle locale reste dans la pile réseau de la machine.
Les adresses IPv4 privées nécessitent un routage adapté pour joindre Internet ;
IPv6 offre un espace d'adressage beaucoup plus vaste. La route par défaut sert
quand aucune route plus précise ne correspond à la destination.

`getent hosts` consulte les sources de résolution configurées par NSS, qui
peuvent inclure les fichiers locaux et DNS. La table des voisins associe les
adresses réseau aux informations de liaison des voisins connus. Un socket
TCP en écoute attend des connexions ; sa présence ne prouve pas qu'un pare-feu
ou le réseau autorise effectivement les connexions distantes.

## Documentation consultée

- [ip](https://man7.org/linux/man-pages/man8/ip.8.html)
- [ping](https://man7.org/linux/man-pages/man8/ping.8.html)
- [getent](https://man7.org/linux/man-pages/man1/getent.1.html)
- [ss](https://man7.org/linux/man-pages/man8/ss.8.html)
