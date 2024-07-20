# Training Networks July 24th and 25th 2024

### TP : Découverte de l'encapsulation des protocoles avec Wireshark

#### Objectifs pédagogiques
- Comprendre le concept d'encapsulation des protocoles dans le modèle OSI.
- Identifier et analyser les différents niveaux de protocoles (Ethernet, IP, ICMP, TCP, UDP, HTTP, HTTPS) dans une capture de trafic réseau.
- Utiliser Wireshark pour capturer et examiner des paquets réseau.

#### Pré-requis
- Installation de Wireshark sur les ordinateurs des apprenants.
- Connaissance de base du modèle OSI et des principaux protocoles réseau.

#### Matériel nécessaire
- Ordinateurs avec Wireshark installé.
- Connexion Internet pour générer du trafic HTTP/HTTPS.

#### Durée
- 45 minutes.

### Étapes du TP

#### Partie 1 : Introduction et préparation (15 minutes)

1. **Présentation de Wireshark :**
   - Expliquez brièvement l'outil Wireshark et ses fonctionnalités principales.
   - Montrez comment sélectionner une interface réseau pour capturer du trafic.

2. **Préparation à la capture :**
   - Démarrez Wireshark et sélectionnez l'interface réseau active (Wi-Fi ou Ethernet).
   - Cliquez sur "Start" pour commencer la capture de trafic.

#### Partie 2 : Capture de trafic réseau (15 minutes)

![PROTOCOLES](./Images/Encapsulation_Protocoles.jpg)
*d'après Wikipedia*

1. **Générer du trafic HTTP/HTTPS :**
   - Ouvrez un navigateur web et visitez plusieurs sites web pour générer du trafic HTTP et HTTPS.

2. **Générer du trafic ICMP :**
   - Ouvrez un terminal ou l'invite de commandes et exécutez la commande `ping www.google.com`.

3. **Générer du trafic TCP/UDP :**
   - Utilisez des applications ou services connus pour utiliser des connexions TCP et UDP, comme le téléchargement d'un fichier ou le streaming de vidéos (Voir l'outil NetworkStuff)

4. **Arrêter la capture :**
   - Revenez à Wireshark et cliquez sur le bouton "Stop" pour arrêter la capture de trafic.

#### Partie 3 : Analyse de la capture (50 minutes)

1. **Filtrage des paquets :**
   - Utilisez les filtres suivants pour isoler les différents types de trafic :
     - Ethernet : `eth`
     - IP : `ip`
     - ICMP : `icmp`
     - TCP : `tcp`
     - UDP : `udp`
     - HTTP : `http`
     - HTTPS : `tls`

2. **Examiner les paquets Ethernet :**
   - Appliquez le filtre `eth` et sélectionnez un paquet.
   - Notez les adresses MAC source et destination, ainsi que le type de protocole.

3. **Examiner les paquets IP :**
   - Appliquez le filtre `ip` et sélectionnez un paquet.
   - Notez les adresses IP source et destination, et le champ Protocole.

4. **Examiner les paquets ICMP :**
   - Appliquez le filtre `icmp` et sélectionnez un paquet.
   - Notez le type et le code ICMP.

5. **Examiner les paquets TCP :**
   - Appliquez le filtre `tcp` et sélectionnez un paquet.
   - Notez les ports source et destination, les numéros de séquence et d'accusé de réception.

6. **Examiner les paquets UDP :**
   - Appliquez le filtre `udp` et sélectionnez un paquet.
   - Notez les ports source et destination.

7. **Examiner les paquets HTTP :**
   - Appliquez le filtre `http` et sélectionnez un paquet.
   - Notez la méthode HTTP, l'URL, et le statut de la réponse.

8. **Examiner les paquets HTTPS :**
   - Appliquez le filtre `tls` et sélectionnez un paquet.
   - Notez les informations disponibles malgré le chiffrement (ex. la négociation TLS).

#### Partie 4 : Discussion et conclusion (10 minutes)

1. **Discussion en groupe :**
   - Discutez des observations faites pendant l'analyse.
   - Mettez en évidence comment chaque couche encapsule les données de la couche supérieure.

2. **Questions et réponses :**

3. **Conclusion :**
   - Récapitulez les points clés de l'activité.
   - Soulignez l'importance de l'encapsulation et des différentes couches de protocoles.

### Masques Réseaux en IPv4 et Notation CIDR: Synthèse

#### Introduction
Les masques réseaux et la notation CIDR (Classless Inter-Domain Routing) sont essentiels pour la gestion et la structuration des réseaux IP. Ils permettent de segmenter les réseaux en sous-réseaux et de gérer efficacement l'adressage IP.

#### Masques Réseaux en IPv4
Un **masque réseau** est une séquence de 32 bits utilisée pour diviser une adresse IP en deux parties: l'adresse du réseau et l'adresse de l'hôte. Il est souvent représenté sous forme de quatre octets décimaux, par exemple, `255.255.255.0`.

- **Fonctionnement**: 
  - Les bits à `1` dans le masque réseau désignent la partie réseau de l'adresse IP.
  - Les bits à `0` désignent la partie hôte.

**Exemple**:
Pour l'adresse IP `192.168.1.10` avec un masque réseau `255.255.255.0`:
- Partie réseau: `192.168.1`
- Partie hôte: `10`

#### Classes d'Adresses IP et Masques Réseaux
Historiquement, les adresses IPv4 étaient divisées en classes (A, B, C, D, E), chaque classe ayant un masque réseau par défaut:
- **Classe A**: `255.0.0.0`
- **Classe B**: `255.255.0.0`
- **Classe C**: `255.255.255.0`

#### Notation CIDR (Classless Inter-Domain Routing)
La **notation CIDR** est une méthode plus flexible pour représenter les réseaux et sous-réseaux. Elle utilise une adresse IP suivie d'un slash (/) et du nombre de bits `1` dans le masque réseau.

- **Exemple de Notation CIDR**:
  - `192.168.1.0/24` signifie que les 24 premiers bits de l'adresse IP sont utilisés pour la partie réseau, équivalent au masque `255.255.255.0`.

#### Avantages de la Notation CIDR
- **Flexibilité**: Permet de créer des sous-réseaux de taille variable, optimisant ainsi l'utilisation des adresses IP.
- **Efficacité**: Réduit le gaspillage d'adresses IP en permettant une allocation plus précise.

#### Conversion entre Notation CIDR et Masques Réseaux
- `255.0.0.0` = `/8`
- `255.255.0.0` = `/16`
- `255.255.255.0` = `/24`
- `255.255.255.128` = `/25`

#### Exemple d'Utilisation de la Notation CIDR
1. **Division d'un Réseau en Sous-Réseaux**:
   - Réseau: `192.168.1.0/24`
   - Sous-réseaux possibles:
     - `192.168.1.0/26` (64 adresses)
     - `192.168.1.64/26` (64 adresses)
     - `192.168.1.128/26` (64 adresses)
     - `192.168.1.192/26` (64 adresses)

2. **Routeur et CIDR**:
   - Un routeur peut être configuré pour acheminer des paquets vers des sous-réseaux spécifiques en utilisant la notation CIDR pour réduire les entrées de routage.

#### Conclusion
Les masques réseaux et la notation CIDR sont des outils puissants pour la gestion des adresses IP dans un réseau. La transition vers la notation CIDR a permis une utilisation plus efficiente des adresses IP et une meilleure flexibilité dans la création et la gestion des sous-réseaux, facilitant ainsi la scalabilité et l'organisation des réseaux modernes.

### Synthèse sur les Adresses IPv4 Privées pour les Classes A, B et C

#### Introduction
Les adresses IP privées sont utilisées au sein des réseaux locaux (LAN) pour permettre la communication entre les appareils sans nécessiter une adresse IP publique unique pour chaque appareil. Ces adresses ne sont pas routables sur l'internet public, ce qui améliore la sécurité et permet une réutilisation efficace des adresses IP. Les plages d'adresses IPv4 privées sont définies par la RFC 1918.

#### Plages d'Adresses IPv4 Privées

1. **Classe A**:
   - **Plage d'adresses**: `10.0.0.0` à `10.255.255.255`
   - **Masque par défaut**: `255.0.0.0` (notation CIDR: `/8`)
   - **Nombre d'adresses disponibles**: 16 777 216 adresses (2^24)
   - **Utilisation typique**: Idéale pour les très grands réseaux, tels que les campus universitaires ou les entreprises avec plusieurs sites.

2. **Classe B**:
   - **Plage d'adresses**: `172.16.0.0` à `172.31.255.255`
   - **Masque par défaut**: `255.240.0.0` (notation CIDR: `/12`)
   - **Nombre d'adresses disponibles**: 1 048 576 adresses (2^20)
   - **Utilisation typique**: Convient aux réseaux de taille moyenne à grande, tels que les réseaux d'entreprise multi-sites.

3. **Classe C**:
   - **Plage d'adresses**: `192.168.0.0` à `192.168.255.255`
   - **Masque par défaut**: `255.255.255.0` (notation CIDR: `/24`)
   - **Nombre d'adresses disponibles**: 65 536 adresses (2^16)
   - **Utilisation typique**: Idéale pour les petits réseaux, tels que les réseaux domestiques ou les petites entreprises.

#### Caractéristiques et Avantages des Adresses Privées

- **Sécurité**: Les adresses privées ne sont pas routables sur l'internet public, ce qui protège les appareils locaux des accès directs depuis l'extérieur.
- **Économie d'adresses**: Permet de conserver les adresses IPv4 publiques en évitant de gaspiller des adresses uniques pour chaque appareil connecté à l'internet.
- **NAT (Network Address Translation)**: Les routeurs utilisent NAT pour permettre aux appareils avec des adresses IP privées de communiquer avec l'internet public via une adresse IP publique partagée.
- **Flexibilité**: Facilite la création de sous-réseaux et la gestion d'adresses IP au sein d'une organisation.

#### Exemple d'Utilisation

1. **Réseau Domestique**:
   - Utilisation d'une plage d'adresses privées de Classe C, par exemple `192.168.1.0/24`, pour connecter des ordinateurs, des imprimantes, des smartphones, etc.
   - Le routeur utilise NAT pour permettre aux appareils de se connecter à l'internet avec une seule adresse IP publique.

2. **Réseau d'Entreprise**:
   - Utilisation d'une plage d'adresses privées de Classe B, par exemple `172.16.0.0/16`, pour un réseau multi-sites.
   - Les différentes sous-réseaux peuvent être créés à l'aide de sous-réseaux plus petits, par exemple `172.16.1.0/24`, `172.16.2.0/24`, etc.

3. **Campus Universitaire**:
   - Utilisation d'une plage d'adresses privées de Classe A, par exemple `10.0.0.0/8`, pour un campus avec des milliers d'appareils connectés.
   - Segmentation du réseau en plusieurs sous-réseaux pour une gestion et une organisation efficaces.

#### Conclusion
Les adresses IPv4 privées pour les classes A, B et C jouent un rôle crucial dans la gestion des réseaux internes, offrant sécurité, flexibilité et une utilisation efficace des adresses IP. Elles permettent aux organisations de tous types et de toutes tailles de structurer leurs réseaux de manière efficace, tout en conservant les adresses IP publiques pour les communications externes.

# VLAN
### Synthèse sur les VLAN

#### Définition
Un VLAN (Virtual Local Area Network) est une technologie qui permet de segmenter un réseau physique en plusieurs réseaux logiques distincts. Les VLAN permettent de regrouper des périphériques réseau situés à des endroits différents comme s'ils faisaient partie du même réseau local.

#### Avantages
1. **Sécurité** : Les VLAN permettent de segmenter le trafic, limitant ainsi les possibilités d'accès non autorisé.
2. **Performance** : En réduisant le domaine de diffusion, les VLAN diminuent le trafic inutile et améliorent les performances du réseau.
3. **Flexibilité** : Les VLAN permettent une gestion plus souple des ressources réseau en facilitant l'ajout ou le déplacement de périphériques sans nécessiter de changements physiques.
4. **Gestion simplifiée** : Ils simplifient l'administration du réseau en regroupant les utilisateurs selon leurs fonctions ou leurs besoins de sécurité.

#### Fonctionnement
- **Tagging** : Les VLAN utilisent des étiquettes (tags) pour identifier les trames appartenant à un VLAN spécifique. Le standard le plus courant pour le tagging VLAN est IEEE 802.1Q.
- **Ports Access et Trunk** :
  - **Ports Access** : Un port access est associé à un seul VLAN et reçoit des trames non étiquetées.
  - **Ports Trunk** : Un port trunk peut transporter des trames de plusieurs VLANs, chaque trame étant étiquetée avec l'identifiant VLAN approprié.

#### Types de VLAN
1. **Data VLAN** : Utilisé pour le trafic utilisateur.
2. **Voice VLAN** : Réservé au trafic VoIP pour assurer une qualité de service adéquate.
3. **Management VLAN** : Utilisé pour le trafic de gestion du réseau, tel que l'administration des switchs et routeurs.
4. **Native VLAN** : Utilisé pour les trames non étiquetées sur un port trunk.

#### Configuration
La configuration des VLAN se fait principalement sur les commutateurs réseau (switches). Les étapes générales incluent :
1. Créer le VLAN sur le switch.
2. Assigner des ports au VLAN.
3. Configurer les ports comme access ou trunk.

#### Exemples de commandes (Cisco IOS)
- **Créer un VLAN** : `vlan 10`
- **Nommer un VLAN** : `name VLAN10`
- **Assigner un port à un VLAN** : `interface fa0/1`, `switchport mode access`, `switchport access vlan 10`
- **Configurer un port trunk** : `interface fa0/24`, `switchport mode trunk`, `switchport trunk allowed vlan 10,20,30`

### Quizz sur les VLAN

#### Questions
1. Qu'est-ce qu'un VLAN ?
2. Quel est le principal avantage des VLAN en termes de sécurité ?
3. Quelle est la norme la plus courante pour le tagging des VLAN ?
4. Quelle est la différence entre un port access et un port trunk ?
5. Nommez deux types de VLAN autres que les VLAN de données.
6. Comment les trames sont-elles identifiées dans un VLAN ?
7. Que signifie le terme "Native VLAN" ?
8. Quelle commande est utilisée pour assigner un port à un VLAN spécifique sur un switch Cisco ?

#### Correction
1. **Qu'est-ce qu'un VLAN ?**
   Un VLAN (Virtual Local Area Network) est une technologie qui permet de segmenter un réseau physique en plusieurs réseaux logiques distincts.

2. **Quel est le principal avantage des VLAN en termes de sécurité ?**
   Les VLAN permettent de segmenter le trafic, limitant ainsi les possibilités d'accès non autorisé.

3. **Quelle est la norme la plus courante pour le tagging des VLAN ?**
   La norme la plus courante pour le tagging des VLAN est IEEE 802.1Q.

4. **Quelle est la différence entre un port access et un port trunk ?**
   Un port access est associé à un seul VLAN et reçoit des trames non étiquetées, tandis qu'un port trunk peut transporter des trames de plusieurs VLANs, chaque trame étant étiquetée avec l'identifiant VLAN approprié.

5. **Nommez deux types de VLAN autres que les VLAN de données.**
   Voice VLAN et Management VLAN.

6. **Comment les trames sont-elles identifiées dans un VLAN ?**
   Les trames sont identifiées par des étiquettes (tags) VLAN.

7. **Que signifie le terme "Native VLAN" ?**
   Le Native VLAN est utilisé pour les trames non étiquetées sur un port trunk.

8. **Quelle commande est utilisée pour assigner un port à un VLAN spécifique sur un switch Cisco ?**
   `switchport access vlan [numéro_du_vlan]`.

   ### QCM sur les VLAN

#### Questions

1. **Qu'est-ce qu'un VLAN ?**
   - A. Un type de commutateur réseau.
   - B. Un réseau physique distinct.
   - C. Un réseau logique virtuel.
   - D. Une méthode de cryptage de données.

2. **Quel est le principal avantage des VLAN en termes de sécurité ?**
   - A. Ils augmentent la bande passante.
   - B. Ils limitent l'accès non autorisé.
   - C. Ils réduisent les coûts matériels.
   - D. Ils facilitent l'accès à internet.

3. **Quelle est la norme la plus courante pour le tagging des VLAN ?**
   - A. IEEE 802.11
   - B. IEEE 802.3
   - C. IEEE 802.1Q
   - D. IEEE 802.1X

4. **Quelle est la différence principale entre un port access et un port trunk ?**
   - A. Un port access est pour les VLAN multiples, un port trunk est pour un seul VLAN.
   - B. Un port access est pour un seul VLAN, un port trunk est pour les VLAN multiples.
   - C. Un port access est plus rapide qu'un port trunk.
   - D. Un port trunk est utilisé uniquement pour les serveurs.

5. **Quels types de VLAN existent ? (Choisissez deux)**
   - A. VLAN de données
   - B. VLAN de sécurité
   - C. VLAN de test
   - D. Voice VLAN

6. **Comment les trames sont-elles identifiées dans un VLAN ?**
   - A. Par leur adresse IP
   - B. Par leur adresse MAC
   - C. Par des étiquettes (tags) VLAN
   - D. Par leur contenu

7. **Que signifie le terme "Native VLAN" ?**
   - A. Le VLAN par défaut pour les trames étiquetées.
   - B. Le VLAN par défaut pour les trames non étiquetées.
   - C. Le VLAN utilisé pour la gestion du réseau.
   - D. Le VLAN utilisé uniquement pour le trafic voix.

8. **Quelle commande est utilisée pour créer un VLAN sur un switch Cisco ?**
   - A. `vlan create 10`
   - B. `vlan add 10`
   - C. `vlan 10`
   - D. `vlan setup 10`

9. **Quel est le rôle principal d'un Voice VLAN ?**
   - A. Séparer le trafic voix du trafic données.
   - B. Sécuriser les communications voix.
   - C. Augmenter la bande passante pour le trafic voix.
   - D. Permettre la gestion des appels internationaux.

10. **Quelle est la commande pour configurer un port en mode trunk sur un switch Cisco ?**
    - A. `switchport mode access`
    - B. `switchport mode trunk`
    - C. `switchport access vlan`
    - D. `switchport vlan trunk`

#### Correction

1. **Qu'est-ce qu'un VLAN ?**
   - C. Un réseau logique virtuel.

2. **Quel est le principal avantage des VLAN en termes de sécurité ?**
   - B. Ils limitent l'accès non autorisé.

3. **Quelle est la norme la plus courante pour le tagging des VLAN ?**
   - C. IEEE 802.1Q

4. **Quelle est la différence principale entre un port access et un port trunk ?**
   - B. Un port access est pour un seul VLAN, un port trunk est pour les VLAN multiples.

5. **Quels types de VLAN existent ? (Choisissez deux)**
   - A. VLAN de données
   - D. Voice VLAN

6. **Comment les trames sont-elles identifiées dans un VLAN ?**
   - C. Par des étiquettes (tags) VLAN

7. **Que signifie le terme "Native VLAN" ?**
   - B. Le VLAN par défaut pour les trames non étiquetées.

8. **Quelle commande est utilisée pour créer un VLAN sur un switch Cisco ?**
   - C. `vlan 10`

9. **Quel est le rôle principal d'un Voice VLAN ?**
   - A. Séparer le trafic voix du trafic données.

10. **Quelle est la commande pour configurer un port en mode trunk sur un switch Cisco ?**
    - B. `switchport mode trunk`

### VLAN par Port

#### Définition
Le VLAN par port, également connu sous le nom de VLAN statique, est une méthode de configuration des VLANs où chaque port d'un commutateur est associé manuellement à un VLAN spécifique. Les périphériques connectés à ces ports sont alors membres de ce VLAN particulier, quelle que soit leur adresse MAC ou tout autre critère.

#### Avantages

1. **Simplicité de Configuration** : La configuration des VLANs par port est simple et directe. Les administrateurs réseau assignent chaque port à un VLAN spécifique via des commandes simples sur le commutateur.
2. **Facilité de Gestion** : Il est facile de visualiser et de gérer la topologie VLAN en se basant sur les ports du commutateur, ce qui facilite la documentation et le dépannage.
3. **Sécurité** : En isolant les ports dans différents VLANs, il est possible de segmenter le réseau de manière à limiter l'accès à certaines ressources, augmentant ainsi la sécurité.
4. **Prévisibilité** : La liaison des ports à des VLANs spécifiques rend le comportement du réseau plus prévisible, car les connexions sont fixes et ne changent pas dynamiquement.

#### Inconvénients

1. **Manque de Flexibilité** : Tout changement dans la topologie réseau, comme le déplacement de périphériques, nécessite une reconfiguration manuelle des ports VLAN, ce qui peut être fastidieux et sujet à des erreurs.
2. **Scalabilité Limitée** : Pour les réseaux de grande taille avec de nombreux utilisateurs ou périphériques mobiles, la gestion des VLANs par port peut devenir ingérable et difficile à maintenir.
3. **Temps de Gestion** : La configuration et la maintenance des VLANs par port nécessitent un temps de gestion plus important, surtout dans des environnements dynamiques où les périphériques sont souvent ajoutés ou déplacés.
4. **Complexité Accrue dans les Environnements Dynamiques** : Dans les environnements où les utilisateurs ou les périphériques changent fréquemment de place, la configuration manuelle des VLANs par port peut devenir complexe et laborieuse.

### Conclusion

Le VLAN par port est une méthode de segmentation réseau facile à comprendre et à mettre en œuvre, particulièrement adaptée aux petits réseaux ou aux environnements où la topologie ne change pas fréquemment. Cependant, dans les réseaux de grande taille ou dynamiques, cette méthode peut devenir difficile à gérer et manque de flexibilité. Les administrateurs réseau doivent peser ces avantages et inconvénients pour déterminer si cette méthode convient à leurs besoins spécifiques.

# SPANNING TREE
### Synthèse sur le Spanning Tree Protocol (STP)

#### Définition
Le Spanning Tree Protocol (STP) est un protocole de réseau de niveau 2 (couche de liaison de données) utilisé pour prévenir les boucles de commutation dans les réseaux locaux (LAN). Les boucles de commutation peuvent entraîner des tempêtes de broadcast, des duplications de trames, et des saturations de la bande passante, rendant le réseau inutilisable.

#### Fonctionnement
STP fonctionne en créant une arborescence logique (spanning tree) à partir de la topologie physique du réseau. Il désactive les liens redondants pour garantir qu'il n'y a qu'un seul chemin actif entre deux périphériques du réseau. Les principales étapes du fonctionnement de STP sont les suivantes :

1. **Élection du Root Bridge** : Le switch avec le Bridge ID le plus bas est élu Root Bridge.
2. **Calcul des coûts de chemin** : Chaque switch calcule le coût du chemin vers le Root Bridge.
3. **Sélection des Root Ports** : Chaque switch sélectionne un Root Port, qui est le port avec le chemin le plus court vers le Root Bridge.
4. **Sélection des Designated Ports** : Pour chaque segment réseau, un seul port est désigné pour acheminer les trames vers et depuis ce segment.
5. **Blocage des ports redondants** : Les ports non désignés et non root sont mis en état de blocage pour éviter les boucles.

#### États des ports dans STP
Les ports peuvent se trouver dans l'un des états suivants :
- **Blocking** : Le port ne transfère pas de données, il écoute seulement les BPDU (Bridge Protocol Data Units).
- **Listening** : Le port prépare la transition vers l'état suivant, il ne transfère toujours pas de données mais peut envoyer et recevoir des BPDUs.
- **Learning** : Le port apprend les adresses MAC mais ne transfère toujours pas de données utilisateur.
- **Forwarding** : Le port transfère les données et apprend les adresses MAC.
- **Disabled** : Le port ne participe pas au STP et ne transfère pas de données.

#### Avantages
- **Prévention des boucles** : STP empêche les boucles dans le réseau, assurant ainsi un fonctionnement stable.
- **Redondance** : En cas de défaillance d'un lien, STP peut réactiver les liens redondants pour maintenir la connectivité.
- **Automatisation** : STP configure automatiquement les chemins optimaux sans intervention humaine.

#### Types de Spanning Tree Protocol
- **STP (802.1D)** : La version originale, introduite en 1990.
- **RSTP (802.1w)** : Rapid Spanning Tree Protocol, introduit en 2001, qui offre des temps de convergence plus rapides.
- **MSTP (802.1s)** : Multiple Spanning Tree Protocol, qui permet plusieurs instances de spanning tree pour différents VLANs.

### Exemple de Configuration STP sur un Switch D-Link

#### Modèle : DGS-1210-28

Pour configurer le Spanning Tree Protocol sur un commutateur D-Link, voici un exemple de configuration :

1. **Connexion au switch** : Connectez-vous au switch via l'interface web ou en utilisant un terminal console.

2. **Activer STP** :
   - **Interface Web** :
     1. Connectez-vous à l'interface web du switch.
     2. Allez dans la section "Spanning Tree" ou "STP" sous le menu de configuration.
     3. Activez STP globalement sur le switch.
     4. Configurez les paramètres globaux tels que le mode (STP, RSTP, MSTP) et le Bridge Priority.

   - **Interface CLI** :
     ```plaintext
     DGS-1210-28:admin# configure
     DGS-1210-28:config# spanning-tree
     DGS-1210-28:config# spanning-tree mode rstp
     DGS-1210-28:config# spanning-tree priority 4096
     ```

3. **Configurer les ports STP** :
   - **Interface Web** :
     1. Allez dans la section "Port Settings" sous "Spanning Tree".
     2. Configurez les paramètres spécifiques des ports comme le coût du chemin et l'état (Edge Port si connecté à un périphérique de fin).

   - **Interface CLI** :
     ```plaintext
     DGS-1210-28:config# interface ethernet 1/1
     DGS-1210-28:config-if# spanning-tree port-priority 128
     DGS-1210-28:config-if# spanning-tree cost 20000
     DGS-1210-28:config-if# spanning-tree edge-port
     ```

4. **Vérifier la configuration** :
   - **Interface Web** :
     1. Vérifiez l'état du spanning tree dans la section de statut.
     2. Assurez-vous que les ports et le root bridge sont correctement configurés.

   - **Interface CLI** :
     ```plaintext
     DGS-1210-28# show spanning-tree
     ```

Ce guide offre une vue d'ensemble pour configurer STP sur un switch D-Link, garantissant ainsi une protection efficace contre les boucles de commutation et une amélioration de la résilience du réseau.

### QCM sur le Spanning Tree Protocol (STP)

#### Questions

1. **Quel est le but principal du Spanning Tree Protocol (STP) ?**
   - A. Augmenter la bande passante du réseau.
   - B. Empêcher les boucles de commutation.
   - C. Améliorer la sécurité des données.
   - D. Simplifier la configuration des VLANs.

2. **Quel état de port STP ne transfère pas de données mais écoute uniquement les BPDUs ?**
   - A. Forwarding
   - B. Learning
   - C. Blocking
   - D. Listening

3. **Quel commutateur est élu comme Root Bridge dans STP ?**
   - A. Le commutateur avec le plus grand ID de bridge.
   - B. Le commutateur avec le plus petit ID de bridge.
   - C. Le commutateur avec le plus grand nombre de ports.
   - D. Le commutateur avec le plus faible coût de chemin.

4. **Quel protocole est une version améliorée de STP avec des temps de convergence plus rapides ?**
   - A. MSTP
   - B. RSTP
   - C. PVST+
   - D. 802.1Q

5. **Quelle commande permet de vérifier l'état du spanning tree sur un switch D-Link via CLI ?**
   - A. `show spanning-tree`
   - B. `spanning-tree status`
   - C. `display spanning-tree`
   - D. `check spanning-tree`

6. **Dans quel état un port STP apprend-il les adresses MAC mais ne transfère pas encore de données ?**
   - A. Forwarding
   - B. Learning
   - C. Blocking
   - D. Listening

7. **Quelle est la fonction d'un port désigné dans STP ?**
   - A. Transférer les données uniquement vers le Root Bridge.
   - B. Transférer les données dans un segment réseau spécifique.
   - C. Transférer les BPDUs uniquement.
   - D. Bloquer le trafic pour éviter les boucles.

8. **Quel protocole permet la gestion de plusieurs instances de spanning tree pour différents VLANs ?**
   - A. STP
   - B. RSTP
   - C. MSTP
   - D. LACP

9. **Quel état n'est pas un état STP valide ?**
   - A. Forwarding
   - B. Listening
   - C. Checking
   - D. Blocking

10. **Quelle action doit être prise pour activer STP sur un switch D-Link via l'interface CLI ?**
    - A. `stp enable`
    - B. `spanning-tree activate`
    - C. `spanning-tree`
    - D. `enable stp`

#### Correction

1. **Quel est le but principal du Spanning Tree Protocol (STP) ?**
   - B. Empêcher les boucles de commutation.

2. **Quel état de port STP ne transfère pas de données mais écoute uniquement les BPDUs ?**
   - C. Blocking

3. **Quel commutateur est élu comme Root Bridge dans STP ?**
   - B. Le commutateur avec le plus petit ID de bridge.

4. **Quel protocole est une version améliorée de STP avec des temps de convergence plus rapides ?**
   - B. RSTP

5. **Quelle commande permet de vérifier l'état du spanning tree sur un switch D-Link via CLI ?**
   - A. `show spanning-tree`

6. **Dans quel état un port STP apprend-il les adresses MAC mais ne transfère pas encore de données ?**
   - B. Learning

7. **Quelle est la fonction d'un port désigné dans STP ?**
   - B. Transférer les données dans un segment réseau spécifique.

8. **Quel protocole permet la gestion de plusieurs instances de spanning tree pour différents VLANs ?**
   - C. MSTP

9. **Quel état n'est pas un état STP valide ?**
   - C. Checking

10. **Quelle action doit être prise pour activer STP sur un switch D-Link via l'interface CLI ?**
    - C. `spanning-tree`


# Interconnexion des switchs
## Interfaces GBIC 
![SFP SX](./Images/20211217222425548701d13b3e4f34bfee9e6c3bc9747e.webp)

![SFP SX](./Images/Simplex-BiDi-SFP-vs-Duplex-SFP.jpg)

La principale différence entre les SFP SX et LX réside dans la longueur d'onde utilisée et la distance de transmission prise en charge.
 > SFP SX (Short Wavelength)
- Utilisent une longueur d'onde courte de 850 nm.
- Conçus pour une utilisation sur fibre optique multimode.
- Prennent en charge des distances allant jusqu'à 550 mètres sur fibre multimode.
- Idéaux pour les connexions intra-bâtiment et les réseaux locaux (LAN).
- Moins coûteux que les SFP LX.

>SFP LX (Long Wavelength)
- Utilisent une longueur d'onde plus longue de 1310 nm.
- Conçus pour une utilisation sur fibre optique monomode.
- Prennent en charge des distances allant jusqu'à 10 km sur fibre monomode.
- Conviennent mieux pour les connexions inter-bâtiments et les réseaux métropolitains.
- Plus coûteux que les SFP SX mais offrent une plus grande portée.
- En résumé, les SFP SX sont optimisés pour les courtes distances sur fibre multimode, tandis que les SFP LX permettent des liaisons plus longues sur fibre monomode. - - Le choix dépend de la distance à couvrir et du type de fibre optique utilisé dans le réseau.



# QOS 
### Synthèse sur la Qualité de Service (QoS)

#### Définition
La Qualité de Service (QoS) est un ensemble de technologies et de mécanismes permettant de garantir des performances réseau spécifiques pour différents types de trafic. QoS est crucial dans les réseaux où la bande passante est partagée entre diverses applications et services, en particulier ceux qui ont des exigences strictes en matière de latence, de gigue et de perte de paquets, comme la VoIP, la vidéo en streaming et les applications critiques d'entreprise.

#### Principe de Fonctionnement
Le principe de fonctionnement de la QoS repose sur plusieurs étapes clés :

1. **Classification** : Identification et marquage des paquets en fonction de leur type de trafic. Cela peut se faire par des critères tels que les adresses IP, les ports TCP/UDP, les protocoles ou les applications.
   
2. **Marquage** : Ajout d'étiquettes ou de marquages aux paquets pour indiquer leur priorité. Les méthodes courantes de marquage incluent DSCP (Differentiated Services Code Point) et CoS (Class of Service).

3. **Mise en File d'Attente et Priorisation** : Utilisation de files d'attente différentes pour traiter les paquets en fonction de leur priorité. Les algorithmes de planification, comme le Weighted Fair Queuing (WFQ) ou le Low Latency Queuing (LLQ), sont utilisés pour garantir que les paquets de haute priorité sont transmis en premier.

4. **Contrôle de la Bande Passante (Policing et Shaping)** : Limitation de la bande passante utilisée par certains types de trafic (policing) ou lissage du trafic pour éviter les pics de bande passante (shaping).

5. **Gestion de la Congestion** : Mécanismes pour gérer et minimiser la congestion du réseau, comme le RED (Random Early Detection) ou WRED (Weighted RED).

#### Avantages
1. **Amélioration de la Performance des Applications Critiques** : Les applications sensibles à la latence et à la bande passante, comme la VoIP et les vidéos, fonctionnent mieux grâce à la priorisation.
   
2. **Optimisation de l'Utilisation de la Bande Passante** : QoS permet une utilisation plus efficace de la bande passante disponible, en évitant que les applications non critiques n'étouffent les ressources réseau.
   
3. **Fiabilité du Réseau** : En garantissant des niveaux de service minimum pour certains types de trafic, QoS augmente la fiabilité globale du réseau.
   
4. **Expérience Utilisateur Améliorée** : Les utilisateurs bénéficient de meilleures performances et d'une qualité constante pour les applications critiques.

#### Activation de QoS

L'activation de QoS varie en fonction des équipements et des environnements réseau, mais les étapes générales incluent :

1. **Configuration des Classes de Service** :
   - Définissez les classes de service en fonction des types de trafic que vous souhaitez prioriser.
   - Par exemple, créez des classes pour la VoIP, le streaming vidéo, les applications d'entreprise, etc.

2. **Marquage du Trafic** :
   - Utilisez des mécanismes de marquage comme DSCP pour identifier les paquets appartenant à chaque classe de service.
   - Exemple de marquage DSCP pour VoIP : `EF (Expedited Forwarding)`.

3. **Configuration des Politiques de QoS** :
   - Définissez des politiques pour la gestion de la bande passante, la mise en file d'attente et la gestion de la congestion.
   - Utilisez des outils comme les Access Control Lists (ACL) pour appliquer ces politiques aux paquets marqués.

4. **Application des Politiques sur les Interfaces Réseau** :
   - Appliquez les politiques de QoS sur les interfaces réseau où le contrôle du trafic est nécessaire.
   - Exemple de configuration sur un routeur Cisco :
     ```plaintext
     class-map match-all VOIP
       match ip dscp ef
     policy-map QOS_POLICY
       class VOIP
         priority percent 30
       class class-default
         fair-queue
     interface GigabitEthernet0/1
       service-policy output QOS_POLICY
     ```

5. **Vérification et Surveillance** :
   - Utilisez des outils de surveillance pour vérifier que les politiques de QoS sont appliquées correctement et que les performances du réseau sont conformes aux attentes.
   - Ajustez les politiques si nécessaire en fonction des besoins en bande passante et des performances observées.

### Conclusion
La QoS est une composante essentielle des réseaux modernes, en particulier pour les environnements où la bande passante est partagée entre de nombreuses applications ayant des besoins différents. En permettant la classification, la priorisation, le marquage et la gestion du trafic réseau, QoS assure une meilleure performance, une utilisation optimisée de la bande passante et une expérience utilisateur améliorée.
# Tables ARP
### Synthèse sur les Tables ARP

#### Définition
ARP (Address Resolution Protocol) est un protocole utilisé pour mapper les adresses IP à des adresses MAC sur un réseau local. Les tables ARP, ou cache ARP, sont des bases de données temporaires stockant les correspondances entre les adresses IP et les adresses MAC. Lorsqu'un périphérique veut communiquer avec un autre sur le même réseau, il utilise ARP pour trouver l'adresse MAC associée à l'adresse IP cible.

#### Fonctionnement
1. **Demande ARP** : Lorsqu'un périphérique A veut envoyer des données à un périphérique B, il envoie une requête ARP en broadcast pour demander l'adresse MAC associée à l'adresse IP de B.
2. **Réponse ARP** : Le périphérique B répond en unicast avec son adresse MAC.
3. **Mise à jour de la table ARP** : A ajoute l'association IP-MAC de B à sa table ARP pour des communications futures. La table ARP est mise à jour périodiquement pour éviter des entrées obsolètes.

#### Importance
Les tables ARP sont cruciales pour le fonctionnement efficace des réseaux locaux. Elles permettent :
- Une résolution rapide des adresses.
- Une réduction des requêtes ARP en broadcast, minimisant ainsi le trafic réseau inutile.

### Commandes ARP Essentielles sous Windows

| **Commande**             | **Description**                                                    |
|--------------------------|--------------------------------------------------------------------|
| `arp -a`                 | Affiche toutes les entrées de la table ARP.                        |
| `arp -s <IP> <MAC>`      | Ajoute une entrée statique dans la table ARP.                      |
| `arp -d <IP>`            | Supprime une entrée de la table ARP.                               |
| `arp -v`                 | Affiche les détails des entrées ARP, y compris les interfaces.     |
| `arp -N <interface>`     | Affiche les entrées ARP pour une interface réseau spécifique.      |
| `arp -d *`               | Supprime toutes les entrées dynamiques de la table ARP.            |

### Exemples d'utilisation

1. **Afficher la table ARP** :
   ```plaintext
   arp -a
   ```
   Cette commande montre toutes les entrées ARP actuelles, y compris les adresses IP, les adresses MAC associées et l'interface réseau.

2. **Ajouter une entrée statique** :
   ```plaintext
   arp -s 192.168.1.10 00-AA-BB-CC-DD-EE
   ```
   Cette commande associe de manière permanente l'adresse IP 192.168.1.10 à l'adresse MAC 00-AA-BB-CC-DD-EE.

3. **Supprimer une entrée** :
   ```plaintext
   arp -d 192.168.1.10
   ```
   Cette commande supprime l'entrée associée à l'adresse IP 192.168.1.10 de la table ARP.

4. **Afficher les entrées ARP d'une interface spécifique** :
   ```plaintext
   arp -N 192.168.1.1
   ```
   Cette commande affiche les entrées ARP associées à l'interface réseau avec l'adresse IP 192.168.1.1.

Les tables ARP sont essentielles pour le bon fonctionnement des réseaux locaux, et les commandes ARP sous Windows permettent aux administrateurs de gérer et de dépanner ces tables efficacement.
# Routeurs

# Outils logiciels
## Networkstuff

## iPerf

## Mobaxterm

test


