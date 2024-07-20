"# TrainingNetworks July 24th and 25th 2024" 
### Activité : Découverte de l'encapsulation des protocoles avec Wireshark

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
- 1 heure.

### Étapes de l'activité

#### Étape 1 : Introduction à Wireshark (10 minutes)
- Présenter brièvement Wireshark, son utilité et ses fonctionnalités.
- Expliquer comment capturer du trafic réseau en sélectionnant une interface réseau appropriée.

#### Étape 2 : Capture de trafic réseau (15 minutes)
1. **Lancer Wireshark :**
   - Ouvrez Wireshark.
   - Sélectionnez l'interface réseau qui est connectée à Internet (par exemple, Wi-Fi ou Ethernet).
   - Cliquez sur le bouton "Start" pour commencer la capture de trafic.

2. **Générer du trafic réseau :**
   - Ouvrez un navigateur web et accédez à plusieurs sites web pour générer du trafic HTTP et HTTPS.
   - Pinguez une adresse IP (par exemple, `ping www.google.com`) pour générer des paquets ICMP.
   - Téléchargez un petit fichier pour générer du trafic TCP et UDP.

3. **Arrêter la capture :**
   - Retournez à Wireshark et cliquez sur le bouton "Stop" pour arrêter la capture.

#### Étape 3 : Analyse de la capture (25 minutes)
1. **Filtrer et examiner les paquets :**
   - Utilisez des filtres pour isoler différents types de trafic :
     - Ethernet : `eth`
     - IP : `ip`
     - ICMP : `icmp`
     - TCP : `tcp`
     - UDP : `udp`
     - HTTP : `http`
     - HTTPS : `tls`

2. **Analyse des paquets :**
   - Sélectionnez un paquet pour chaque type de protocole et examinez les détails dans le panneau inférieur de Wireshark.
   - Notez les différentes couches de l'encapsulation pour chaque type de paquet. Par exemple :
     - Un paquet HTTP sera encapsulé dans TCP, qui est encapsulé dans IP, qui est encapsulé dans Ethernet.

3. **Observation des en-têtes :**
   - Pour chaque type de protocole, identifiez et expliquez les champs importants dans les en-têtes. Par exemple :
     - **Ethernet** : Adresse MAC source et destination, Type de protocole.
     - **IP** : Adresse IP source et destination, Protocole (ICMP, TCP, UDP).
     - **ICMP** : Type et code ICMP, checksum.
     - **TCP** : Ports source et destination, numéro de séquence, accusé de réception.
     - **UDP** : Ports source et destination, longueur, checksum.
     - **HTTP/HTTPS** : Méthode HTTP, URL, statut de la réponse.

#### Étape 4 : Discussion et conclusion (10 minutes)
- Discutez avec les apprenants des observations faites pendant l'analyse.
- Soulignez l'importance de l'encapsulation et de la séparation des différentes couches de protocoles.
- Répondez aux questions et clarifiez les points confus.

#### Notes supplémentaires
- Encourager les apprenants à expérimenter avec d'autres types de trafic et à utiliser des filtres Wireshark pour isoler et examiner ces paquets.
- Souligner les différences entre HTTP et HTTPS (notamment l'encapsulation supplémentaire due à TLS).

### Résumé de l'activité
Cette activité permet aux apprenants de visualiser concrètement comment les protocoles réseau sont encapsulés les uns dans les autres, et de comprendre comment utiliser Wireshark pour analyser le trafic réseau. Elle combine des explications théoriques avec une pratique concrète, facilitant ainsi l'assimilation des concepts clés en réseaux et télécommunications.