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
- 1 heure 30 minutes.

### Étapes du TP

#### Partie 1 : Introduction et préparation (15 minutes)

1. **Présentation de Wireshark :**
   - Expliquez brièvement l'outil Wireshark et ses fonctionnalités principales.
   - Montrez comment sélectionner une interface réseau pour capturer du trafic.

2. **Préparation à la capture :**
   - Démarrez Wireshark et sélectionnez l'interface réseau active (Wi-Fi ou Ethernet).
   - Cliquez sur "Start" pour commencer la capture de trafic.

#### Partie 2 : Capture de trafic réseau (15 minutes)

1. **Générer du trafic HTTP/HTTPS :**
   - Ouvrez un navigateur web et visitez plusieurs sites web pour générer du trafic HTTP et HTTPS.

2. **Générer du trafic ICMP :**
   - Ouvrez un terminal ou l'invite de commandes et exécutez la commande `ping www.google.com`.

3. **Générer du trafic TCP/UDP :**
   - Utilisez des applications ou services connus pour utiliser des connexions TCP et UDP, comme le téléchargement d'un fichier ou le streaming de vidéos.

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
   - Encouragez les apprenants à poser des questions pour clarifier leurs doutes.
   - Répondez aux questions et fournissez des explications supplémentaires si nécessaire.

3. **Conclusion :**
   - Récapitulez les points clés de l'activité.
   - Soulignez l'importance de l'encapsulation et des différentes couches de protocoles.

### Résumé du TP

Ce TP permet aux apprenants de comprendre l'encapsulation des protocoles réseau en utilisant Wireshark pour capturer et analyser du trafic réseau. En passant par les différents filtres et en examinant les paquets, les apprenants visualisent comment chaque protocole encapsule les données du protocole de la couche supérieure, offrant une compréhension pratique et concrète du modèle OSI.