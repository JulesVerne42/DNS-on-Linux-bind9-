## Labo DNS avec Bind9

### Dans ce tuto nous allons mettre en place un labo composé de :  
- un serveur DNS sous **Debian 12**  
- un client sous **Debian 12**  
- L'installation et la configuration du package **Bind9**
> Les adresses IP, CIDR, nom de carte réseau et nom de domaine/sous-domaine sont à modifier suivant votre application.

### Configuration IP des deux machines
#### Serveur DNS sous Debian 12
##### Modification du fichier "*interfaces*"
- Nom de la carte réseau `enp0s3`  
- Etat de la carte réseau `static`  
- Adresse IP du serveur DNS `10.0.0.5`  
- Adresse IP de la passerelle `10.0.0.1`  
- CIDR `/24`  
![1_interfaces](https://github.com/user-attachments/assets/394ed49c-1d95-441e-8faa-8aa1acb4d77d)

#### Client sous Debian 12
##### Modification du fichier "*interfaces*"
- Nom de la carte réseau `enpos3`  
- Etat de la carte réseau `static`  
- Adresse IP du client `10.0.0.20`  
- Adresse IP de la passerelle `10.0.0.1`  
- CIDR `/24`  
![1 1_interfaces](https://github.com/user-attachments/assets/63eed0df-0131-4896-bdf8-5976c81997fa)

##### Modification du fichier "*resolv.conf*"
- Domaine de recherche `wilders.lan`  
- Adresse IP du DNS `10.0.0.5`  
![1 2_resolv conf](https://github.com/user-attachments/assets/44700d32-d211-493e-a337-53966d2cc2d5)

### Installation du package DNS
Sur votre serveur DNS mettre a jour le système et installer le package **Bind9**  
- `sudo apt update && sudo apt upgrade`  
- `sudo apt install bind9 bind9-doc`  

### Editions des fichiers de configurations présent dans "*/etc/bind*"
:warning: Attention à la syntaxe, les fichiers de configs sont sensibles !!  
#### Modification du fichier "*named.conf.options*"
- Réseau `10.0.0.0/24`
- Autorisation de requête DNS `localhost; internal-network;`  
- Autorisation de transfert DNS `localhost;`  
- Redirection DNS `8.8.8.8;`  
- Autorisation de requête récursive `yes;`  






