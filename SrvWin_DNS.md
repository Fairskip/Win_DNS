# 1. Installation du Service DNS sur le serveur

Ajout de rôle et de fonctionnalités > [Assistant Ajout de rôle et de fonctionnalités](https://github.com/Fairskip/Win_DNS/blob/main/DNS%20Install%201.png) :
* Avant de commencer => suivant
* Type d'installation => par défaut, suivant
* Sélection du serveur => par défaut, suivant
* Rôles de serveur => Serveur DNS _et_ Services AD DS, suivant
* ... jusqu'à la fin => par défaut, suivant, installer

<br>

# 2. Zone wilders.lan

DNS => clic droit > Gestionnaire de DNS  

![gestionnaire dns](https://github.com/Fairskip/Win_DNS/blob/main/Gestionnaire%20DNS.png)

### 1 - Zone de recherche directe  

* Gestionnaire DNS > SRV-QuestWin > Zones de recherche directes => Clic droit, [nouvelle zone](https://github.com/Fairskip/Win_DNS/blob/main/Zone%20de%20recherche%201.png)
* Assistant Nouvelle zone :
	* Bienvenue ! => suivant
	* Type de zone => défaut, suivant
	* Nom de la zone => wilders.lan, suivant
	* Fichier zone => défaut (wilders.lan.dns), suivant
	* ... jusqu'à la fin =>  par défaut, suivant/terminer

![result](https://github.com/Fairskip/Win_DNS/blob/main/Zone%20de%20recherche%205.png) 

### 2 - Zone de recherches inversées  

* Gestionnaire DNS > SRV-QuestWin > Zones de recherche inversée => Clic droit, [nouvelle zone](https://github.com/Fairskip/Win_DNS/blob/main/Zone%20de%20recherche%20inversee%201.png)
* Assistant Nouvelle zone :  
	* Bienvenue ! => suivant
	* Type de zone => défaut, suivant
	* Nom de la zone de recherche inversée => Zone de recherche  inversée IPv4, suivant
	* Nom de la zone de recherche inversée => [ID réseau : 172.20.0](https://github.com/Fairskip/Win_DNS/blob/main/Zone%20de%20recherche%20inversee%203.png)
	* Fichier zone => défaut, suivant
	* ... jusqu'à la fin =>  par défaut, suivant/terminer  

<br>

# 3. Créer un registre A pour le serveur et le Host ayant une réservation IP fixe
### 1 - Serveur

* Gestionnaire DNS > SRV-QuestWin > Zones de recherche directes > wilders.lan => Clic droit, [Nouvel hôte (A ou AAAA)](https://github.com/Fairskip/Win_DNS/blob/main/Hote%20A%201.png) 
* Nouvel hôte :
	* Nom : Quest
	* Adresse IP : 172.20.0.254
	* [Créer un pointeur d'enregistrement PTR associé => à cocher](https://github.com/Fairskip/Win_DNS/blob/main/Hote%20A%202.png) puis 
* Ajouter un hôte.


### 2 - Host

* Nouvel hôte :
	* Nom : windy
	* Adresse IP : 172.20.0.10
	* Créer un pointeur d'enregistrement PTR associé => à cocher, ajouter, ok, [terminé](https://github.com/Fairskip/Win_DNS/blob/main/Hote%20A%204.png) 

![result](https://github.com/Fairskip/Win_DNS/blob/main/Hote%20A%206.png)    

![result](https://github.com/Fairskip/Win_DNS/blob/main/Hote%20A%20inversee.png)

<br>

# 4. Créer un CNAME pour le serveur  

* Gestionnaire DNS > SRV-QuestWin > Zones de recherche directes > wilders.lan => Clic droit, [Nouvel alias (CNAME)](https://github.com/Fairskip/Win_DNS/blob/main/Cname%201.png)
* Nouvel enregistrement de ressource : 
	* Nom de l'alias => dns
	* Nom de domaine pleinement qualifié (FQDN) => dns.wilders.lan
	* Nom de domaine complet (FQDN) => Parcourir
   
	* [Parcourir](https://github.com/Fairskip/Win_DNS/blob/main/Cname%202.png) :
   
				* SRV-QuestWin => double clic
				* Zones de recherche => double clic
				* wilders.lan => clic Quest, ok
				* ok
* Ok  

![result](https://github.com/Fairskip/Win_DNS/blob/main/Cname%205.png)

<br>

# 5. Test
### 1 - Test depuis Server  

* Résolution de Nom 
* Résolution inverse

![test](https://github.com/Fairskip/Win_DNS/blob/main/Reseau_dns_servertest.png)

### 2 - Test depuis Windy (host windows) 

* Résolution de Nom
* Résolution inverse

![test](https://github.com/Fairskip/Win_DNS/blob/main/Reseau_dns_hosttest.png)
