# Guide Complet Docker – Du Débutant à l’Expert

Docker est un outil de conteneurisation qui a révolutionné la façon dont nous construisons, distribuons et exécutons les applications. Ce guide **ultra-complet** est structuré en chapitres progressifs, du niveau débutant à expert. Chaque chapitre fournit des explications détaillées, des exemples concrets, des commandes prêtes à l’emploi, des checklists pour éviter les erreurs et des meilleures pratiques. Vous pourrez ainsi acquérir pas à pas une maîtrise approfondie de Docker et de son écosystème.

## 1. Introduction générale 

Dans ce chapitre d’introduction, nous découvrirons **pourquoi Docker est devenu si populaire** et quels sont ses avantages clés. Nous aborderons également les **cas d’usage** types de la conteneurisation.

### 1.1 Qu’est-ce que Docker ? Pourquoi l’utiliser ?

Docker est une plateforme de conteneurisation qui permet d’encapsuler une application et toutes ses dépendances dans un conteneur léger et portable. Contrairement aux machines virtuelles traditionnelles, les conteneurs partagent le noyau du système hôte, ce qui les rend plus **légers** et **rapides** à démarrer.

**Avantages de Docker :**

- **Portabilité** : “It works on my machine!” – Docker élimine ce problème. Une application conteneurisée fonctionne de la même manière sur tout système disposant de Docker (Windows, Mac, Linux, serveurs cloud, etc.), car le conteneur embarque son environnement.
- **Isolation** : Chaque conteneur est isolé des autres. Cela signifie qu’ils n’interfèrent pas entre eux, garantissant une meilleure stabilité (par ex., des versions de bibliothèques différentes peuvent coexister sur la même machine sans conflit).
- **Légèreté et performance** : Les conteneurs sont plus légers que les VM car ils ne nécessitent pas d’embarquer un système d’exploitation complet. Ils démarrent en quelques secondes (voire millisecondes) et consomment moins de ressources.
- **Scalabilité et microservices** : Docker se prête bien à l’architecture microservices. On peut facilement déployer et multiplier des instances de conteneurs pour passer à l’échelle, manuellement ou via des orchestrateurs.
- **Productivité en développement** : Docker simplifie la configuration des environnements de développement et de test. Fini les longues installations – vous pouvez lancer une base de données, un serveur web ou tout autre service en une commande, puis le supprimer sans laisser de trace.

**Cas d’usage courants :**

- **Développement multi-environnements** : Les développeurs utilisent Docker pour homogénéiser les environnements de dev/test/prod. Par exemple, lancer un conteneur de base de données pour les tests unitaires, puis le jeter.
- **Déploiement d’applications** : Emballer une application dans une image Docker et la déployer en conteneur garantit que la même version tourne partout. De plus, on peut déployer des mises à jour en créant une nouvelle image (immutable infrastructure).
- **Microservices et architecture distribuée** : Chaque service (authentification, API, front-end, etc.) peut être containerisé individuellement, facilitant le déploiement distribué et la mise à l’échelle de chaque composant indépendamment.
- **CI/CD** : Intégration dans les pipelines d’intégration continue/déploiement continu. Par exemple, construire l’image Docker d’une application à chaque commit, exécuter les tests dedans, puis la pousser vers un registre pour déploiement.

### 1.2 Docker vs machines virtuelles

Pour bien comprendre Docker, distinguons-le des **machines virtuelles (VM)** traditionnelles :

- Une **VM** embarque un OS complet invité (guest) sur un hyperviseur, avec son kernel, ce qui consomme beaucoup de ressources. Démarrer une VM peut prendre plusieurs minutes.
- Un **conteneur Docker** utilise le kernel de l’OS hôte via des mécanismes d’isolement (namespaces, cgroups…). Il n’embarque que les fichiers et bibliothèques nécessaires à l’application. Résultat : l’empreinte est minime et le démarrage quasi-instantané.

**En résumé** : Docker offre la flexibilité de la virtualisation, sans la lourdeur des VMs. C’est idéal pour livrer rapidement des applications isolées, cohérentes et extensibles.

### 1.3 Checklist – Bien démarrer avec Docker (Introduction)

- **✓ Comprendre le concept** : Docker = conteneurs légers pour applications + dépendances, isolation sans virtualisation complète.
- **✓ Identifier vos cas d’usage** : Environnement de dev reproductible, déploiement portable, microservices, etc.
- **✓ Vérifier la compatibilité** : Avoir un système prenant en charge Docker (Linux natif, ou Docker Desktop sur Windows/Mac).
- **✓ Vocabulaire de base** : Savoir ce qu’est une *image* (modèle statique) vs un *conteneur* (instance en cours d’exécution), on détaillera cela plus loin.
- **✓ Compte Docker Hub (optionnel)** : Créez un compte sur Docker Hub pour télécharger des images et éventuellement héberger les vôtres.

---

## 2. Installation et configuration

Ce chapitre explique **comment installer Docker** sur les principales plateformes (Windows, macOS, Linux) pas à pas. Vous y trouverez des instructions détaillées, des commandes prêtes à exécuter et des conseils de configuration initiale.

### 2.1 Installer Docker sur Windows

Sur Windows, Docker est fourni via **Docker Desktop** qui inclut le moteur Docker et une interface de gestion.

**Prérequis Windows :**

- Windows 10 ou 11 (édition Pro ou Famille) à jour.
- **WSL 2** (Windows Subsystem for Linux) activé pour un fonctionnement optimal (Docker Desktop l’utilise en arrière-plan sur Windows Home/Famille notamment).
- La virtualisation matérielle activée (VT-x / AMD-V) dans le BIOS.

**Étapes d’installation :**

1. **Télécharger Docker Desktop** : Rendez-vous sur la page officielle de Docker et téléchargez l’installateur Docker Desktop pour Windows.
2. **Exécuter l’installateur** : Lancez le fichier `.exe` téléchargé et suivez l’assistant. Cochez l’option pour utiliser WSL2 au lieu de Hyper-V si proposé (WSL2 est généralement recommandé).
3. **Finaliser et lancer** : Une fois l’installation terminée, Docker Desktop se lance. Une icône baleine apparaît dans la barre de notification. Docker va finaliser la configuration (il peut vous demander d’installer/activer WSL2 si ce n’est pas déjà fait).
4. **Vérifier l’installation** : Ouvrez un terminal PowerShell ou l’invite de commande et tapez :  
   ```powershell
   docker --version
   ```  
   Cela doit afficher le numéro de version de Docker installée.
5. **Test rapide** : Exécutez un conteneur de test :  
   ```powershell
   docker run hello-world
   ```  
   Ce conteneur de test téléchargera une petite image et affichera un message de succès si tout fonctionne.

**Tips Windows :**

- *WSL2 et Docker* : Si vous êtes sur Windows 10 Famille, Docker Desktop utilisera WSL2 (il installera une distribution Linux légère en arrière-plan). Assurez-vous d’avoir activé WSL2 au préalable (`wsl --install` active par défaut WSL2 sur Windows 10/11 récents).
- *Docker Toolbox* : Pour les anciennes versions de Windows non compatibles Hyper-V/WSL2, il existait Docker Toolbox, mais il est obsolète. Mettez plutôt à niveau Windows si possible.

### 2.2 Installer Docker sur macOS

Sur Mac, l’installation se fait également via **Docker Desktop pour Mac**.

**Prérequis macOS :**

- macOS 10.15 (Catalina) ou supérieur recommandé.
- Compte utilisateur avec droits d’administration (pour installer les applications).
- Virtualisation activée (Docker Desktop utilise HyperKit ou Apple Hypervisor Framework en coulisse).

**Étapes d’installation :**

1. **Télécharger Docker Desktop** : Depuis le site officiel de Docker, téléchargez l’image disque Docker Desktop pour Mac (`.dmg`).
2. **Installation** : Ouvrez le fichier `.dmg` puis glissez l’icône Docker vers le dossier Applications.
3. **Lancer Docker** : Ouvrez Docker depuis Applications. La première fois, MacOS peut demander des autorisations d’accès (réseau, fichiers). Acceptez pour permettre à Docker de fonctionner.
4. **Vérifier** : Docker apparaît dans la barre de menus (icône de baleine). En ligne de commande (Terminal), vérifiez :  
   ```bash
   docker --version
   ```  
   Et testez :  
   ```bash
   docker run hello-world
   ```  
   Vous devriez voir le message de succès de Docker Hello World.

**Tips macOS :**

- *Apple Silicon (M1/M2)* : Docker Desktop supporte les Macs Apple Silicon (basés sur ARM64). Assurez-vous de télécharger la version adéquate. La plupart des images Docker populaires proposent maintenant des builds multi-architecture (amd64/arm64), Docker choisira la bonne variante automatiquement.
- *Homebrew (optionnel)* : Si vous utilisez Homebrew, vous pouvez installer Docker Desktop avec la commande :  
  ```bash
  brew install --cask docker
  ```  
  (Cela installe l’app Docker Desktop – il faudra toujours la lancer pour démarrer le service Docker.)

### 2.3 Installer Docker sur Linux

Docker Engine a été initialement conçu pour Linux, l’installation y est donc très bien supportée. Les méthodes varient légèrement selon la distribution. 

**Prérequis généraux Linux :**

- Un noyau Linux récent (3.10+), la plupart des distributions modernes sont compatibles.
- Droits `root` ou sudo pour installer les paquets.

**Option A – Installation via le gestionnaire de paquets (ex: Ubuntu/Debian) :**

Sur Ubuntu, Debian et dérivés, Docker est disponible via le dépôt officiel de Docker. Voici les étapes pour Ubuntu (versions récentes 20.04/22.04 LTS) :

1. **Installer les prérequis** (outils d’ajout de dépôts et certificats) :  
   ```bash
   sudo apt update
   sudo apt install -y apt-transport-https ca-certificates curl gnupg lsb-release
   ```
2. **Ajouter la clé GPG de Docker** :  
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   ```
3. **Ajouter le dépôt Docker stable** :  
   ```bash
   echo \
     "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
     https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
     sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```
4. **Installer Docker Engine** :  
   ```bash
   sudo apt update
   sudo apt install -y docker-ce docker-ce-cli containerd.io
   ```
5. **Ajouter votre utilisateur au groupe Docker (optionnel)** : Pour exécuter Docker sans sudo (convenable en dev, à éviter en prod), ajoutez l’utilisateur courant au groupe `docker` :  
   ```bash
   sudo usermod -aG docker $USER
   ```  
   *Note :* Il faudra se déconnecter/reconnecter pour que ce changement prenne effet.
6. **Vérifier l’installation** :  
   ```bash
   docker --version
   docker run hello-world
   ```  
   La commande Hello World doit afficher un message confirmant le bon fonctionnement.

**Option B – Installation via le script automatique :**

Docker propose un script d’installation automatique, pratique pour les tests ou si vous voulez aller vite :  
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```  
Ce script détecte la distribution et installe Docker Engine. (Utilisez-le de préférence sur des VM de test, pour de la production il est conseillé de comprendre et maîtriser les paquets installés.)

**Option C – Autres distributions :**  
- Sur CentOS / Fedora : Utilisez `dnf`/`yum` avec le dépôt officiel Docker (similaire à Ubuntu). Par exemple sur CentOS7 : installer `yum-utils` puis `sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo` et installez `docker-ce`.
- Sur Arch Linux : Docker peut s’installer via `pacman -S docker`.
- … Pour d’autres systèmes, consultez la documentation officielle.

### 2.4 Configuration initiale de Docker

Une fois Docker installé, quelques configurations de base peuvent améliorer votre expérience :

- **Démarrage du service** : Sur Linux, assurez-vous que le service Docker est démarré et activé au boot :  
  ```bash
  sudo systemctl enable --now docker
  ```  
  (Sur Windows/Mac, Docker Desktop gère cela automatiquement.)
- **Miroirs de registre** : Si votre connexion à Docker Hub est lente ou si vous êtes en entreprise, vous pouvez configurer des miroirs (dans `/etc/docker/daemon.json` sur Linux ou via l’UI Docker Desktop).
- **Espace disque** : Par défaut Docker stocke ses images/volumes sous `/var/lib/docker` (Linux) ou dans une image disque dédiée (Docker Desktop). Assurez-vous d’avoir assez d’espace ou changez l’emplacement si nécessaire.
- **Proxy** : Si vous êtes derrière un proxy, configurez-le pour Docker (variables d’environnement `HTTP_PROXY`/`HTTPS_PROXY` pour le service Docker).
- **Mises à jour** : Mettez Docker à jour régulièrement (`sudo apt upgrade docker-ce` ou via Docker Desktop > Check for updates) pour bénéficier des derniers correctifs et fonctionnalités.

### 2.5 Checklist – Installation

- **✓ Prérequis vérifiés** : OS compatible, virtualisation activée, accès admin/sudo.
- **✓ Docker installé** : Via Docker Desktop (Win/Mac) ou paquets (Linux). Aucune erreur pendant l’install.
- **✓ Post-install** : Sur Linux, ajouté au groupe docker (si souhaité), service démarré.
- **✓ Test de fonctionnement** : `docker run hello-world` réussi.
- **✓ Environnement prêt** : Espace disque suffisant, configuration proxy/mirroir effectuée si nécessaire.
- **⚠️ Erreurs courantes** : Oubli d’activer WSL2 sur Windows, ne pas relancer sa session Linux après ajout au groupe docker (erreur “permission denied” lors de `docker run`), espace disque saturé par `/var/lib/docker`.

---

## 3. Concepts clés et premières commandes

Maintenant que Docker est installé, passons aux **concepts de base** : images, conteneurs, volumes, réseaux. Dans ce chapitre, nous expliquons progressivement ces notions fondamentales, illustrées par des **commandes Docker de base** et des exemples concrets.

### 3.1 Images et conteneurs : Comprendre la différence

Deux termes reviennent sans cesse avec Docker : **image** et **conteneur**. Il est crucial de bien les distinguer :

- **Image Docker** : Une image est un modèle “figé”, un package qui contient tout le nécessaire pour faire tourner une application (code, runtime, bibliothèques, variables par défaut…). C’est un peu l’équivalent d’une **classe** (en programmation) ou d’un snapshot d’OS. Une image est construite (build) à partir d’un Dockerfile ou téléchargée depuis un registre (Docker Hub, etc.). Les images sont **immutables** : chaque image a un identifiant (hash) et peut être versionnée via des *tags* (ex: `python:3.9-alpine` est une image de Python v3.9 basée sur Alpine).
- **Conteneur Docker** : Un conteneur est une **instance en cours d’exécution** d’une image. Si l’image est le modèle, le conteneur est l’objet créé à partir de ce modèle. Le conteneur ajoute une couche en lecture/écriture par dessus l’image immuable pour y stocker les modifications (fichiers créés/modifiés pendant l’exécution). Un conteneur a son propre système de fichiers isolé, ses propres processus, son interface réseau (en isolation relative), tout en partageant le noyau du système hôte.

**Cycle de vie basique :** On tire ("pull") ou construit une image, puis on la *lance* ("run") pour créer un conteneur. Quand on n’en a plus besoin, on peut arrêter le conteneur et le supprimer, mais l’image reste disponible pour en lancer d’autres.

**Exemple concret :** Docker fournit l’image de test `hello-world`. Lorsqu’on exécute :  
```bash
docker run hello-world
```  
Docker va chercher l’image `hello-world` sur Docker Hub (si elle n’est pas déjà en cache), puis créer un conteneur à partir de cette image et exécuter le programme qui affiche "Hello from Docker". Le conteneur s’arrête ensuite automatiquement (car l’application se termine). 

Voyons de plus près la commande `docker run` et d’autres commandes essentielles :

### 3.2 Premières commandes Docker essentielles

Voici un tour d’horizon des commandes de base pour manipuler images et conteneurs :

- **Télécharger une image** :  
  ```bash
  docker pull <nom_image>:<tag>
  ```  
  Exemple :  
  ```bash
  docker pull nginx:latest
  ```  
  Si aucun tag n’est précisé, Docker prend `latest` par défaut. Cette commande télécharge l’image (ici Nginx) depuis Docker Hub (par défaut) et la stocke localement.

- **Lister les images locales** :  
  ```bash
  docker images
  ```  
  ou  
  ```bash
  docker image ls
  ```  
  Cela affiche les images Docker présentes sur votre machine, avec leurs tags et taille.

- **Lancer un conteneur** :  
  ```bash
  docker run [options] <image> [commande]
  ```  
  C’est *la* commande principale. Par exemple :  
  ```bash
  docker run nginx
  ```  
  Cela lance un conteneur à partir de l’image `nginx:latest`. Sans option particulière, ce conteneur tourne en arrière-plan et Nginx démarre (serveur web).  
  Autre exemple plus interactif :  
  ```bash
  docker run -it ubuntu bash
  ```  
  *Options expliquées :* `-it` combine `-i` (mode interactif) et `-t` (pseudo-TTY). Ici, on lance un conteneur Ubuntu et on démarre `bash` à l’intérieur, obtenant un shell interactif. Vous vous retrouvez *dans* le conteneur (le prompt change). Tapez `exit` pour quitter et arrêter le conteneur.

- **Lister les conteneurs** :  
  ```bash
  docker ps
  ```  
  (équivalent à `docker container ls`). Par défaut, n’affiche que les conteneurs actifs. Ajoutez `-a` pour voir **tous** les conteneurs (y compris ceux stoppés) : `docker ps -a`.

- **Arrêter un conteneur** :  
  ```bash
  docker stop <nom_ou_id_du_conteneur>
  ```  
  Le nom du conteneur peut être spécifié ou son identifiant unique (vous le voyez via `docker ps`). Exemple : `docker stop fervent_goldberg` (Docker donne par défaut des noms aléatoires amusants aux conteneurs si vous ne spécifiez pas `--name` à la création).

- **Redémarrer un conteneur** (stoppé) :  
  ```bash
  docker start <nom_ou_id>
  ```  
  Ceci redémarre un conteneur existant (ex: après un `docker stop`). À noter : `docker run` crée toujours un nouveau conteneur, tandis que `docker start` repart d’un conteneur arrêté.

- **Supprimer un conteneur** :  
  ```bash
  docker rm <nom_ou_id>
  ```  
  Supprime l’enregistrement du conteneur (son système de fichiers isolé, ses méta-données...). Il faut d’abord qu’il soit stoppé (on peut forcer avec `-f` pour kill + remove en une commande). Exemple : `docker rm fervent_goldberg`.

- **Supprimer une image** :  
  ```bash
  docker rmi <image_id_ou_nom:tag>
  ```  
  Cela supprime l’image localement (si aucun conteneur ne l’utilise encore). Vous pouvez obtenir l’`IMAGE ID` avec `docker images`.

- **Inspecter un conteneur** :  
  ```bash
  docker inspect <nom_ou_id>
  ```  
  Retourne un JSON complet avec toutes les informations sur le conteneur (config, montages, IP assignée, etc.). Utile pour du debug ou pour récupérer une info précise via `--format`.

- **Consulter les logs** d’un conteneur :  
  ```bash
  docker logs <nom_ou_id>
  ```  
  Affiche les sorties standard (stdout/stderr) générées par le conteneur (par le process principal à l’intérieur). Ajoutez `-f` pour suivre en continu (tail -f).

- **Exécuter une commande dans un conteneur existant** :  
  ```bash
  docker exec [options] <nom_ou_id> <commande>
  ```  
  Ex : `docker exec -it fervent_goldberg sh` vous donne un shell *dans* un conteneur Linux déjà démarré, sans avoir à démarrer un nouveau conteneur. Très pratique pour inspecter ou débugger l’intérieur d’un conteneur en cours de route.

**Astuces débutant :**  
- Pour éviter de retenir les IDs hexadécimaux, Docker accepte les débuts d’ID uniques. Si `docker ps` montre un conteneur dont l’ID commence par `abc123...`, vous pouvez taper `docker stop abc123` s’il n’y a pas d’ambiguïté. Mieux, utilisez les noms de conteneurs (option `--name` lors de `docker run` pour définir un nom custom).
- Utilisez `docker ps -a -q` combiné à d’autres commandes pour des actions massives (ex: `docker rm $(docker ps -a -q)` supprime *tous* les conteneurs stoppés, attention !).

### 3.3 Notion de ports, d’environnement et de paramètres

L’une des forces de Docker est de pouvoir personnaliser l’exécution d’un conteneur via des options à `docker run` :

- **Mapping de ports (option -p)** : Par défaut, un conteneur a son propre réseau isolé, ses ports ne sont pas accessibles depuis l’hôte. Pour rendre un service accessible, il faut publier ses ports.  
  Exemple :  
  ```bash
  docker run -d -p 8080:80 nginx
  ```  
  Ici `-d` lance le conteneur en *détaché* (background) et `-p 8080:80` mappe le port 80 du conteneur sur le port 8080 de l’hôte. Ainsi, accéder à `http://localhost:8080` sur votre machine affiche la page servie par Nginx dans le conteneur.
  
  *Syntaxe:* `-p <port_hôte>:<port_conteneur>`. On peut répéter l’option pour plusieurs ports. Attention aux collisions (si un port hôte est déjà pris).

- **Variables d’environnement (option -e)** : Pour passer des configurations au conteneur sans modifier l’image, on utilise des variables d’environnement.  
  Exemple :  
  ```bash
  docker run -d -e MYSQL_ROOT_PASSWORD=secr3t -p 3306:3306 mysql:latest
  ```  
  L’image officielle MySQL lit la variable `MYSQL_ROOT_PASSWORD` pour initialiser le mot de passe root. On l’a fournie via `-e`. On peut passer plusieurs `-e` pour différentes variables ou utiliser `--env-file` pour les charger depuis un fichier.

- **Volumes (option -v)** : (Première intro rapide, on détaillera les volumes en section 3.4).  
  Les données dans un conteneur sont volatiles par défaut (elles disparaissent si le conteneur est supprimé). Pour persister ou partager des fichiers, Docker propose les volumes.  
  Ex :  
  ```bash
  docker run -d -v /mon/repertoire/hote:/data nginx
  ```  
  Montre un répertoire de l’hôte dans le conteneur. Ici, le dossier `/mon/repertoire/hote` sur l’hôte est monté dans le conteneur sur `/data`. Si Nginx écrit dans `/data`, les fichiers apparaîtront sur l’hôte. Inversement, on peut injecter des données initiales depuis l’hôte.  
  On peut aussi utiliser des volumes nommés (ex: `-v nom_volume:/data`), plus sur ce sujet bientôt.

- **Nom du conteneur (option --name)** :  
  Par défaut Docker génère un nom aléatoire. Utilisez `--name mon_nom` pour nommer explicitement le conteneur, ce qui simplifie la gestion (ex: `docker stop mon_nom`).

- **Redémarrage automatique (option --restart)** :  
  Utile en prod pour des conteneurs qui doivent tourner en continu. Par ex:  
  ```bash
  docker run -d --restart unless-stopped apache:latest
  ```  
  Ce conteneur redémarrera automatiquement si le processus s’arrête ou si le système reboot, sauf si on l’a explicitement stoppé.

### 3.4 Volumes : persistance des données

Les **volumes Docker** permettent de sauvegarder des données en dehors du cycle de vie des conteneurs. Sans volume, si un conteneur est supprimé, toutes les données à l’intérieur sont perdues. Avec un volume, les données persistent indépendamment des conteneurs.

Il existe deux grands types de volumes :

- **Volumes nommés (managed volumes)** : Gérés par Docker, stockés dans son répertoire interne (`/var/lib/docker/volumes/...`). On les référence par un nom, Docker se charge de l’emplacement.  
  *Exemple de création et utilisation :*  
  ```bash
  docker volume create mes-donnees
  docker run -d -v mes-donnees:/var/lib/mysql mysql
  ```  
  Ici, on crée un volume `mes-donnees`, puis on lance un MySQL en montant ce volume sur le chemin de la base MySQL (`/var/lib/mysql`). Ainsi, les données de la base seront persistées sur le volume même si le conteneur est détruit ou recréé.

- **Bind mounts (montages d’un dossier hôte)** : Monte un dossier ou fichier du système hôte dans le conteneur. Cela permet par exemple d’accéder à des fichiers locaux depuis un logiciel dans le conteneur.  
  *Exemple :*  
  ```bash
  docker run -it -v /home/user/projet/www:/usr/share/nginx/html nginx
  ```  
  Ici, on monte le dossier local `~/projet/www` dans le conteneur sur le dossier servi par Nginx. Ainsi, Nginx servira directement les fichiers du host. C’est très pratique en dev pour voir ses modifications de code en direct sans reconstruire une image.  
  ⚠️ Attention : les bind mounts dépendent du système de fichiers hôte, ils peuvent poser des problèmes de permissions (ex: utilisateur conteneur vs user hôte) ou de performance (ex: entre Windows/macOS et conteneur Linux via Docker Desktop, les I/O peuvent être plus lentes).

**Commandes utiles pour les volumes :**

- Lister les volumes Docker : `docker volume ls`
- Inspecter un volume (chemin réel etc.) : `docker volume inspect nom_volume`
- Supprimer un volume : `docker volume rm nom_volume` (Attention, supprime définitivement les données si pas sauvegardées ailleurs).
- Nettoyer tous les volumes non utilisés : `docker volume prune` (dangereux à utiliser sans réfléchir, supprime ceux qui ne sont pas montés dans un conteneur actif).

**Bonnes pratiques volumes :**

- Utilisez des volumes pour toute donnée devant survivre aux conteneurs (bases de données, fichiers upload, etc.).
- Préférez les **volumes nommés** pour la portabilité (Docker gère l’emplacement, et sur Windows/macOS il stocke dans une image disque dédiée pour de meilleures perfs).
- Pour le développement, les bind mounts sont pratiques, mais en production ils sont moins portables et peuvent poser des soucis. Si vous les utilisez (par ex. pour config), faites attention aux chemins et permissions.
- Ne montez **jamais** le socket Docker ( `/var/run/docker.sock` ) dans un conteneur à moins de savoir exactement ce que vous faites – c’est un risque de sécurité (ça donne accès illimité à Docker).

### 3.5 Réseaux : communication entre conteneurs

Docker fournit des capacités réseau flexibles. Par défaut, Docker crée un réseau de type "bridge" appelé `bridge` auquel tous les conteneurs sans instruction particulière sont connectés. 

**Types de réseaux Docker :**

- **Bridge (pont)** : C’est le réseau par défaut sur une machine Docker standalone. Chaque conteneur a une IP interne (ex: 172.17.0.X) sur ce réseau. Ils peuvent communiquer entre eux *si* ils sont sur le même réseau bridge utilisateur (le réseau `bridge` par défaut les connecte tous, mais ils ne connaissent pas le nom DNS les uns des autres par défaut). On peut créer des réseaux bridge personnalisés pour isoler des groupes de conteneurs.
- **Host** : Le conteneur partage la pile réseau de l’hôte (pas d’isolation réseau du tout). Utile pour des cas où la performance ou la compatibilité prime et qu’on veut que le conteneur écoute directement sur l’IP de l’hôte. (Ex: pour un conteneur qui doit scanner le réseau local).
- **None** : Pas de réseau du tout (le conteneur n’a pas d’interface réseau). Rarement utilisé, sauf pour isolement extrême ou conteneurs qui n’ont pas besoin de réseau.
- **Overlay** : Réseau multi-hôtes utilisé avec Docker Swarm ou d’autres orchestrateurs. Permet à des conteneurs sur des hôtes différents de communiquer comme s’ils étaient sur le même réseau local virtuel. (On en reparlera dans la section orchestration).

**Commandes réseaux de base :**

- Lister les réseaux Docker :  
  ```bash
  docker network ls
  ```  
  Par défaut, vous verrez `bridge`, `host`, `none`, et possiblement des réseaux créés par Docker Compose ou autres.
- Créer un réseau utilisateur :  
  ```bash
  docker network create mon_reseau
  ```  
  Par défaut, c’est un réseau de type bridge. Vous pouvez spécifier `--driver bridge` explicitement, ou d’autres pilotes.
- Connecter un conteneur à un réseau :  
  - Au lancement :  
    ```bash
    docker run --network mon_reseau --name web1 -d nginx
    ```  
    Ici on connecte directement le conteneur `web1` au réseau `mon_reseau`. S’il y a d’autres conteneurs sur ce réseau, ils pourront se pinguer et même se résoudre par nom (Docker ajoute une entrée DNS interne avec le nom du conteneur).
  - Après coup :  
    ```bash
    docker network connect mon_reseau mon_container
    ```  
    Permet de connecter un conteneur déjà existant (et lancé) à un réseau supplémentaire.
- Déconnecter un conteneur d’un réseau :  
  ```bash
  docker network disconnect mon_reseau mon_container
  ```

**Exemple concret de réseau user-defined :**  
Supposons deux conteneurs, une application web et une base de données, qu’on veut isoler du reste. On peut faire :  
```bash
docker network create backend_net
docker run -d --name db --network backend_net -e POSTGRES_PASSWORD=pass postgres:alpine
docker run -d --name web --network backend_net -p 8080:80 mywebapp:latest
```  
Ici, les conteneurs `db` et `web` sont sur le réseau `backend_net`. Le conteneur `web` peut contacter `db` en utilisant `db:5432` (nom du conteneur comme hostname, 5432 étant le port Postgres). De l’extérieur, seul le port 8080 est exposé (pour accéder au web). La base de données n’est pas exposée sur l’hôte, elle est isolée dans ce réseau interne.

**Bonnes pratiques réseaux :**

- Limitez l’utilisation de `--network host` aux cas nécessaires (on perd l’isolation).
- Utilisez des réseaux bridge **utilisateur** pour segmenter vos applications. Par ex., mettre toutes les parties d’une même application sur un réseau dédié afin qu’elles communiquent entre elles facilement, tout en étant isolées des autres applis.
- Docker DNS interne : sur un réseau user-defined, Docker DNS résout les noms de conteneurs et alias de service (notion qu’on abordera avec Compose). Profitez-en pour ne pas coder en dur des IP !
- Pensez à la **sécurité réseau** : Par défaut, les conteneurs sur un même réseau peuvent tout se dire. Pour un contrôle plus fin, il faut recourir à des outils complémentaires (iptables, ou des features comme les network policies sous Kubernetes).

### 3.6 Exercice pratique : Premier workflow Docker simple

Mettons en pratique ces concepts par un petit scénario concret. Supposez que vous voulez héberger un site web statique avec Nginx, et éditer les fichiers en local :

1. **Pull de l’image Nginx** :  
   ```bash
   docker pull nginx:latest
   ```
2. **Lancer Nginx avec un bind mount** pour servir un répertoire local :  
   - Créez un dossier local `~/site-web` et placez-y un fichier `index.html` (par exemple avec "Hello Docker" dedans).
   - Lancez le conteneur :  
     ```bash
     docker run -d --name monsite -p 8080:80 -v ~/site-web:/usr/share/nginx/html:ro nginx:latest
     ```  
     Options utilisées :  
     - `--name monsite` pour nommer le conteneur.  
     - `-p 8080:80` pour exposer localement.  
     - `-v ~/site-web:/usr/share/nginx/html:ro` pour monter votre site en lecture seule dans Nginx.
3. **Tester** : Ouvrez un navigateur sur `http://localhost:8080`. Vous devriez voir votre page "Hello Docker".
4. **Modifier** : Changez le fichier `index.html` local, sauvegardez, et rafraîchissez le navigateur. La modification apparaît sans devoir redémarrer le conteneur (grâce au bind mount).
5. **Inspecter les logs** :  
   ```bash
   docker logs monsite
   ```  
   Vous y verrez les logs d’accès Nginx quand vous avez navigué.
6. **Nettoyer** : Une fois fini, arrêtez et supprimez le conteneur :  
   ```bash
   docker stop monsite && docker rm monsite
   ```  
   L’image Nginx reste en cache local prête pour un prochain usage.

Cet exercice illustre comment Docker facilite le développement (on a un serveur web opérationnel en une commande) tout en permettant l’édition en direct. On a utilisé plusieurs concepts : image (nginx), conteneur, port mapping, volume (bind), logs.

### 3.7 Checklist – Bases Docker

- **✓ Image vs conteneur clair** : Une image est un modèle, un conteneur est une instance en cours d’exécution.
- **✓ Commandes de base maîtrisées** : `docker run`, `pull`, `ps`, `stop`, `rm`, `logs`, `exec`… S’exercer à les utiliser dans un shell.
- **✓ Ports et données persistantes anticipés** : Utiliser `-p` pour exposer les ports nécessaires, `-v` ou volumes nommés pour les données à conserver.
- **✓ Réseaux bridgés par défaut** : Savoir que sans `-p` le service n’est pas accessible de l’hôte. Comprendre qu’entre conteneurs sur le même réseau user-defined, on peut communiquer via noms de conteneur.
- **✓ Nettoyage** : Penser à nettoyer conteneurs stoppés et images inutiles pour économiser de l’espace (`docker system prune` est une commande tout-en-un pour nettoyer images non utilisées, conteneurs stoppés, volumes orphelins, etc., **à utiliser avec prudence**).
- **⚠️ Pièges débutant à éviter** : Ne pas oublier le `-d` si on veut détacher (sinon on croit que le terminal est figé alors qu’on “est” dans le process du conteneur). Ne pas lancer 2 conteneurs avec le même port hôte (erreur "address already in use"). Ne pas stocker des données importantes dans un conteneur sans volume (elles disparaîtront).

---

## 4. Gestion avancée des images et conteneurs

Après les bases, abordons des aspects **avancés dans la gestion des images et des conteneurs**. Nous verrons comment optimiser les Dockerfiles (pour des images plus efficaces), gérer les logs de conteneurs de manière adéquate, et approfondir l’utilisation des volumes et réseaux au-delà des bases.

### 4.1 Optimisation des Dockerfiles et build d’images

Un **Dockerfile** est un fichier texte qui contient les instructions pour construire une image Docker. Mieux votre Dockerfile est écrit, plus votre image sera légère, sécurisée et rapide à construire. Voici des techniques et meilleures pratiques d’optimisation :

- **Choisir le bon base image** : L’instruction `FROM` définit l’image de base. Choisissez une base adaptée et minimale. Par exemple, pour une appli Node.js, `FROM node:18-alpine` sera beaucoup plus léger que `FROM node:18` (basé sur Debian). Alpine Linux est ultra léger, mais attention à la compatibilité (certains packages peuvent être manquants ou différent, glibc vs musl).
- **Limiter la taille de l’image** : Moins d’outils inutiles = moins de surface d’attaque et de taille. Évitez d’installer des packages non requis. Nettoyez les caches de package managers (apt, yum) après install. Par exemple, dans un Dockerfile Debian :  
  ```Dockerfile
  RUN apt-get update && apt-get install -y build-essential libssl-dev && rm -rf /var/lib/apt/lists/*
  ```  
  Ici, on supprime les listes apt pour économiser de l’espace.
- **Utiliser .dockerignore** : Créez un fichier `.dockerignore` à la racine du contexte de build pour exclure les fichiers qui ne doivent pas être copiés dans l’image (par ex: `.git/`, fichiers de config locaux, caches…). Cela réduit la taille du contexte envoyé au démon Docker et évite d’ajouter accidentellement des secrets.
- **Tirer parti du cache de build** : Docker build met en cache chaque couche. L’ordre de vos instructions est crucial. Mettez les instructions qui changent rarement en haut (pour maximiser la réutilisation du cache) et celles qui changent souvent (ex: copie du code source) vers la fin. Par exemple, si vous faites un `COPY . .` au début, toute modification de code invalidera le cache pour toutes les couches suivantes. Mieux vaut installer les dépendances système avant de copier le code applicatif.
- **Multi-stage builds** : Docker permet les builds multi-étapes (multi-stage). C’est très puissant pour optimiser. L’idée est d’avoir un Dockerfile avec plusieurs `FROM` (stages). Les premiers stages peuvent servir à compiler/construire l’application (avec tous les outils nécessaires), puis un stage final plus épuré ne récupère que l’artifact final. Par ex, pour une appli Go ou Java : compilez dans une image contenant le SDK, puis `COPY` le binaire/jar dans une image de base plus petite (scratch ou jre slim) dans le stage final. Résultat : une image finale beaucoup plus petite et sans outils de build.  
  *Exemple conceptuel :*  
  ```Dockerfile
  FROM maven:3.8-jdk-11 AS build  
  COPY pom.xml .  
  RUN mvn dependency:go-offline  
  COPY src/ src/  
  RUN mvn package  
  FROM openjdk:11-jre-slim  
  COPY --from=build target/myapp.jar /app/myapp.jar  
  CMD ["java", "-jar", "/app/myapp.jar"]
  ```  
  Ici on compile une appli Java avec Maven dans le stage `build`, puis on copie le jar dans une image JRE légère. L’image finale n’a pas Maven ni les sources.
- **Minimiser le nombre de couches** : Chaque instruction Dockerfile (RUN, COPY, ADD…) crée une couche. Combinez les commandes quand c’est logique pour réduire le nombre de couches. Exemple, au lieu de :  
  ```Dockerfile
  RUN apt-get install -y package1  
  RUN apt-get install -y package2  
  ```  
  Faites :  
  ```Dockerfile
  RUN apt-get install -y package1 package2  
  ```  
  ou combinez en une seule commande `RUN` si possible. Mais n’allez pas sacrifier la lisibilité pour quelques couches en moins - trouvez un équilibre.
- **Utiliser des tags explicites** : Quand vous construisez une image (`docker build -t monapp:1.0 .`), taggez-la avec un numéro de version ou un tag clair. Évitez d’avoir trop d’images `<none>` (dangling) à force de re-build sans tag. Utilisez aussi `latest` pour marquer l’image courante, mais toujours avec un tag versionné en parallèle pour la traçabilité.
- **Documenter le Dockerfile** : Utilisez des commentaires `#` pour expliquer les étapes complexes. Et utilisez l’instruction `LABEL` pour inclure des méta-données (auteur, version de l’application, lien git, etc.). Par exemple :  
  ```Dockerfile
  LABEL maintainer="Jean Dupont <jean.dupont@example.com>" \
        version="1.0" \
        description="Mon API en Node.js"
  ```

**Outil utile** : *Hadolint* – un linter pour Dockerfile qui vous signale les bonnes pratiques ou erreurs courantes. Vous pouvez l’utiliser pour analyser votre Dockerfile (il existe en ligne de commande et même en extension éditeur).

### 4.2 Gestion des logs de conteneurs

Dans Docker, les logs des applications à l’intérieur des conteneurs (stdout et stderr) sont capturés par Docker et stockés (par défaut dans des fichiers JSON sur l’hôte). Mal gérés, ces logs peuvent prendre de la place ou être difficiles à consulter.

**Principes de base :**

- Par défaut, tout ce que l’application écrit sur la sortie standard (stdout/stderr) *sera visible via* `docker logs`. Donc, **logguez sur stdout/stderr** dans vos apps containerisées, c’est la façon 12-factor recommandée (plutôt que dans un fichier interne).
- Docker garde ces logs tant que le conteneur existe. Si un conteneur tourne longtemps et loggue beaucoup, le fichier de log peut grossir indéfiniment.

**Options et outils pour les logs :**

- **Limiter la taille des logs** : Docker propose des **drivers de logs**. Le driver par défaut (`json-file`) peut être configuré avec une rotation. Par exemple, pour limiter chaque conteneur à 10Mo de logs sur 3 fichiers max, créez ou modifiez `/etc/docker/daemon.json` comme ceci :  
  ```json
  {
    "log-driver": "json-file",
    "log-opts": {
      "max-size": "10m",
      "max-file": "3"
    }
  }
  ```  
  Puis redémarrez Docker. Ceci évite de saturer le disque.
- **Autres drivers** : Vous pouvez envoyer les logs vers syslog, journald, un service externe (comme Fluentd, logstash, etc.) en changeant le driver. Voir la doc Docker sur les logging drivers.
- **Consulter les logs en direct** : `docker logs -f monconteneur` pour suivre en continu. Vous pouvez aussi ajouter `--tail 100` pour ne voir que les 100 dernières lignes puis suivre.
- **Centraliser les logs multi-conteneurs** : Pour un usage avancé, des outils comme *ELK/EFK stack* (Elasticsearch + Kibana + Fluentd/Logstash) permettent de collecter et centraliser les logs de tous vos conteneurs (via un agent qui utilise le socket Docker ou qui s’intègre en driver). En dev simple, ce n’est pas nécessaire, mais en prod avec des dizaines de conteneurs, c’est très utile.
- **Logs et Docker Compose** : Avec `docker-compose`, un simple `docker-compose logs -f` agrège les logs de tous les conteneurs définis (pratique en dev pour tout voir en une commande).

**Bonnes pratiques logs :**

- Faites régulièrement le ménage des conteneurs stoppés pour supprimer leurs logs (un conteneur supprimé supprime ses logs).
- Ne logguez pas excessivement en mode production (gérez le niveau de logging de vos applis, ex: DEBUG vs INFO).
- Surveillez l’espace disque de `/var/lib/docker/containers/*/*-json.log` si vous restez sur json-file sans rotation – ou configurez la rotation comme vu ci-dessus.

### 4.3 Gestion avancée des volumes

On a déjà vu les bases des volumes. Pour aller plus loin :

- **Volumes nommés vs anonymes** : Un volume déclaré avec juste `-v /chemin` sans nom est un volume **anonyme** – Docker en crée un sans nom qu’il référence par un hash. Ils sont plus difficiles à traquer. Préférez nommer vos volumes pour pouvoir les gérer (sauf usage jetable).
- **Consulter l’espace occupé** : Les volumes peuvent occuper beaucoup d’espace si on y stocke BDD, uploads, etc. Utilisez `docker system df -v` pour voir l’espace utilisé par chaque volume.
- **Backups de volumes** : Puisque les volumes résident sur l’hôte, pensez à sauvegarder les données critiques. On peut faire un backup en tar d’un volume en lançant un conteneur temporaire:  
  ```bash
  docker run --rm -v mon_volume:/data -v $(pwd):/backup alpine \
    tar czf /backup/mon_volume_backup.tgz /data
  ```  
  Ici on utilise une image Alpine pour archiver le contenu du volume `mon_volume` dans le dossier courant.
- **Volumes et Dockerfile** : L’instruction `VOLUME` dans un Dockerfile permet de documenter qu’un certain chemin est prévu pour être un volume. Docker ne crée pas un volume nommé automatiquement pour autant (il crée un volume anonyme à l’exécution si rien n’est monté). Vous pouvez généralement l’ignorer et gérer les volumes via les commandes run/compose.
- **Drivers de volumes** : Docker permet d’utiliser des drivers pour stocker les volumes à l’extérieur : nfs, gluster, amazon EBS, etc. En usage avancé ou en cluster, on peut ainsi garder des données sur un stockage réseau. En local, le driver local suffit.

**Astuce** : Pour explorer le contenu d’un volume nommé, vous pouvez temporairement le monter dans un conteneur outil. Ex:  
```bash
docker run --rm -it -v mon_volume:/data alpine sh
```  
puis à l’intérieur `ls /data` etc. Ceci évite d’avoir à chercher le path system du volume sur l’hôte.

### 4.4 Gestion avancée des réseaux

Allons un peu plus loin sur le réseau Docker :

- **Réseaux utilisateurs bridgés vs default bridge** : Si vous lancez des conteneurs sans préciser de réseau, ils vont sur le réseau `bridge` par défaut. Sur ce réseau, les conteneurs peuvent communiquer *par IP* seulement (il n’y a pas de DNS conteneur->conteneur par défaut sur le réseau `bridge`). C’est pour inciter à utiliser les réseaux user-defined où le DNS fonctionne. Donc pour des applications multi-conteneurs, créez toujours un réseau dédié plutôt que d’utiliser `bridge` par défaut.
- **Réseaux et performance** : Le NAT du réseau bridge ajoute un peu de latence par rapport à `--network host`. Mais généralement c’est négligeable. Si vous faites du high performance networking (ex: trafic à très haut volume), testez éventuellement `host` network.
- **IP fixe (sur un réseau)** : On peut attribuer manuellement une IP à un conteneur sur un réseau docker (`--ip`). Cela peut dépanner mais normalement on préfère s’en remettre au DNS interne et ne pas figer d’IPs.
- **Connecter plusieurs réseaux** : Un conteneur peut être sur plusieurs réseaux. Par exemple, un conteneur peut avoir une interface dans un réseau "front" (exposé à un reverse proxy) et une autre dans un réseau "back" (pour joindre une DB). On le connectera aux deux réseaux. Ce faisant, il a deux IP, une par réseau.
- **Réseaux Macvlan** : Docker supporte le driver macvlan qui permet de donner au conteneur une adresse IP sur le réseau physique de l’hôte (il apparaît comme un device réseau à part entière sur le LAN). C’est utile pour des conteneurs qui doivent être accessibles directement par une IP dédiée sur le réseau local (ex: container qui doit être vu comme un machine à part entière sur le LAN). C’est un cas avancé, qui nécessite de configurer correctement le driver macvlan (attention, l’hôte ne peut pas communiquer directement avec le conteneur dans ce mode sans configuration supplémentaire).

### 4.5 Astuces et bonnes pratiques (Images/Containers avancés)

- **Nettoyage images** : Après avoir expérimenté, vous aurez sans doute accumulé des images inutilisées (dangling). Utilisez `docker image prune` pour les nettoyer. En ajoutant `-a` ça supprime toutes les images non utilisées par un conteneur (dangereux si vous ne voulez pas re-puller plus tard).
- **Tagger et pousser vos images** : Apprenez à tagger (`docker tag`) et à push sur un registre (`docker push`). Même en local, utiliser un registre privé (Artifactory, Harbor, ou simplement Docker Hub en privé) peut vous aider à partager vos images ou les déployer sur d’autres machines.
- **CI de vos Dockerfiles** : Intégrez la construction de vos images dans la CI pour détecter rapidement si un changement casse le Dockerfile. Utilisez `docker build --no-cache` de temps en temps pour valider que votre build réussit sans le cache (simulateur de "from scratch").
- **Conteneurs éphémères** : En prod, traitez vos conteneurs comme éphémères : ils peuvent être tués et recréés à tout moment. Ne conservez rien d’important à l’intérieur (d’où l’importance des volumes/externalisation des données). Une config orchestrée de conteneurs doit pouvoir repartir de zéro (infrastructure immutable).
- **Mise à jour des images de base** : Surveillez les mises à jour de vos images de base (base images). Par exemple, si vous construisez FROM node:14, sachez quand Node 14 arrive en EOL et planifiez de migrer. Docker n’auto-update pas vos images, c’est à vous de reconstruire avec les nouvelles versions.
- **Éviter les conteneurs “chèvres à 5 pattes”** : Un conteneur = un service/app *unique*. Ne pas lancer plusieurs processus différents dans un même conteneur (ex: lancer MySQL et Apache dans la même image). Docker est pensé pour être minimal par conteneur. Use one container per concern, ça facilite la réutilisation et la scalabilité.

### 4.6 Checklist – Gestion avancée

- **✓ Dockerfile optimisé** : Base image minimaliste, instructions ordonnées pour le cache, multi-stage si nécessaire, .dockerignore présent.
- **✓ Images légères** : Pas de bloatware, packages inutiles ou fichiers temporaires restants.
- **✓ Gestion des logs planifiée** : Rotation configurée ou monitoring de la taille, stratégie de collecte si multi-containers.
- **✓ Données en sécurité** : Volumes nommés utilisés pour données persistantes, backup/restauration testés.
- **✓ Réseaux maîtrisés** : Réseaux custom utilisés pour isoler les conteneurs par application, connaissance des modes host/bridge/overlay.
- **✓ Cycle de vie images** : Processus pour nettoyer régulièrement ou archiver les images plus utilisées (prune, etc.).
- **⚠️ Écueils évités** : Dockerfile avec trop de couches inutiles (temps de build et taille qui explosent), logs saturant le disque, conteneur qui “perd” ses données faute de volume, conflit d’IP ou de ports par méconnaissance du networking Docker.

---

## 5. Docker Compose et orchestration (services multi-conteneurs)

Quand vos besoins dépassent un conteneur unique, **Docker Compose** devient un outil indispensable. Ce chapitre couvre Compose en détail, pour définir et orchestrer des applications multi-conteneurs sur une seule machine (typiquement en développement, tests ou petite prod). Nous verrons comment écrire un fichier Compose, les commandes associées, et un exemple concret d’application multi-service.

### 5.1 Introduction à Docker Compose

**Docker Compose** est un outil qui permet de définir et de gérer multi-conteneurs **via un fichier de configuration YAML**. Plutôt que de lancer manuellement plusieurs `docker run` avec plein d’options, on décrit des services dans un fichier `docker-compose.yml` puis on utilise des commandes Compose pour tout démarrer/déterminer en orchestration.

Compose est excellent pour :
- Déclarer les conteneurs d’une application (web, bdd, cache, etc.), leurs images, variables, volumes, réseaux… versionné dans un fichier.
- Gérer le cycle de vie de l’ensemble : `docker-compose up` pour tout démarrer, `docker-compose down` pour arrêter et nettoyer.
- Configurer des liens/réseaux facilement : Compose crée un réseau par défaut pour vos services, ils pourront communiquer par nom de service DNS.
- Reproduire un environnement complet en une commande (pratique pour devs ou CI tests).
- Porter ce même fichier en production (avec Docker Swarm notamment) ou servir de documentation exécutable de votre architecture.

### 5.2 Format du fichier docker-compose.yml

Le cœur de Compose est le **fichier YAML** généralement nommé `docker-compose.yml`. Il décrit les services et options. Voici les sections principales :

- **version** : version du format Compose (ex: "3.8"). Choisissez la plus récente supportée par votre Docker/Compose.
- **services** : c’est ici qu’on définit chaque conteneur (service) de l’application, avec son nom en en-tête.
- **images ou build** : pour chaque service, soit on indique l’image à utiliser (`image: nom:tag`), soit comment construire l’image (`build:` context, Dockerfile).
- **ports** : équivalent du `-p`, pour exposer les ports.
- **environment** : variables d’environnement à passer.
- **volumes** : montages de volumes ou de dossiers.
- **depends_on** : pour indiquer qu’un service dépend d’un autre (compose gère l’ordre de démarrage).
- **networks** : pour configurer des réseaux (sinon compose en crée un par défaut).
- **volumes (top-level)** : optionnellement, on peut déclarer des volumes nommés à utiliser dans les services.
- **deploy** : (utile surtout en mode swarm) pour indiquer des règles de déploiement, réplica, etc. Pas utilisé en local.

**Exemple commenté de docker-compose.yml :**

Supposons une appli web Python Flask avec une base de données PostgreSQL. Notre structure pourrait être :

```yaml
version: "3.8"
services:
  web:
    build: .
    ports:
      - "5000:5000"
    environment:
      - DATABASE_URL=postgresql://postgres:password@db:5432/mydb
    depends_on:
      - db
    volumes:
      - .:/app
  db:
    image: postgres:13
    volumes:
      - db-data:/var/lib/postgresql/data
    environment:
      - POSTGRES_PASSWORD=password
      - POSTGRES_DB=mydb
volumes:
  db-data:
```

Analysons ce fichier :
- Deux services : **web** et **db**.
- `web` n’a pas d’image spécifiée mais un `build: .` – cela indique de construire l’image depuis le Dockerfile présent dans le même dossier (le contexte `.`, Dockerfile par défaut nommé "Dockerfile"). On aurait donc un Dockerfile configurant l’app Flask.
- `ports: "5000:5000"` : on expose le port 5000 du conteneur (Flask) sur le port 5000 hôte.
- `environment` pour `web` contient une variable `DATABASE_URL` pointant vers le service `db` (notez `@db:5432` – le hostname `db` sera résolu vers le conteneur Postgres grâce au réseau Compose).
- `depends_on: - db` : assure que le service `db` est lancé avant `web` (cela ne garantit pas que Postgres soit prêt, mais au moins le conteneur démarre d’abord).
- `volumes` pour `web` : on monte le dossier courant (`.`) dans `/app` (supposons que l’app Flask est dans /app, et le Dockerfile utilise ce code). Ainsi en dev on peut voir les changements sans reconstruire.
- Service **db** utilise l’image officielle Postgres 13.  
- On lui monte un volume nommé `db-data` sur le dossier des données PG, pour persister la base.
- On passe le mot de passe admin et le nom de BDD via des variables.
- En bas, on déclare le volume `db-data` dans la section top-level `volumes:`. Sans cela, Compose le crée quand même automatiquement, mais c’est une bonne pratique de le déclarer si on veut spécifier des options ou simplement documenter.

### 5.3 Commandes Docker Compose de base

Avec un `docker-compose.yml` en place, voici les commandes principales à connaître (à exécuter dans le répertoire contenant le fichier ou en spécifiant `-f chemin/vers/docker-compose.yml`):

- **Démarrer les services** :  
  ```bash
  docker-compose up
  ```  
  Par défaut, `up` démarre en affichant les logs de tous les services dans la console. Ajoutez `-d` pour détacher (comme `docker run -d`).  
  Cette commande va construire les images si besoin, créer les conteneurs, réseaux et volumes, puis lancer les conteneurs.  
  *Astuce:* vous pouvez démarrer un seul service: `docker-compose up -d db` (dans l’exemple précédent, ça ne lancerait que la base de données).

- **Arrêter les services** :  
  Utilisez `Ctrl+C` si vous avez laissé `up` sans `-d` (ça stoppe tout), sinon:  
  ```bash
  docker-compose stop
  ```  
  Cela arrête les conteneurs sans les supprimer.

- **Redémarrer** :  
  ```bash
  docker-compose start
  ```  
  pour redémarrer des conteneurs arrêtés (rarement utilisé sans d’autres commandes, souvent on préfère `up` qui gère tout).

- **Logs combinés** :  
  ```bash
  docker-compose logs -f
  ```  
  Montre les logs de tous les services (précédés du nom du service en préfixe) et suit en continu.

- **Statut** :  
  ```bash
  docker-compose ps
  ```  
  Montre la liste des conteneurs en cours gérés par ce compose (noms, statut, ports mappés...).

- **Exécuter un commande dans un service** :  
  ```bash
  docker-compose exec <service> <commande>
  ```  
  Similaire à `docker exec` mais réfère le service par son nom dans le compose. Ex: `docker-compose exec web bash` ouvre un shell dans le service web (si l’image a bash).

- **Mettre à jour / reconstruire un service** :  
  Si vous modifiez l’image (Dockerfile ou même juste le code si on rebuild l’image), utilisez :  
  ```bash
  docker-compose build web
  docker-compose up -d web
  ```  
  pour reconstruire l’image du service web et recréer le conteneur. Ou simplement `docker-compose up -d --build` pour tout rebâtir si nécessaire et relancer.
  
- **Arrêter et tout supprimer** :  
  ```bash
  docker-compose down
  ```  
  Cela arrête les conteneurs et **supprime** conteneurs, réseaux créés par compose et volumes nommés déclarés dans le fichier (option `-v` assure que les volumes anonymes ou nommés dans volumes: seront aussi supprimés, donc attention aux données). Sans `-v`, il laisse les volumes persistants tranquilles.

**Remarque** : `docker-compose` était historiquement un outil à part. Depuis Docker 20.x, la commande `docker compose` (sans tiret, intégrée au CLI Docker) offre la même fonctionnalité. Selon votre installation, vous utiliserez l’une ou l’autre, mais les concepts restent identiques.

### 5.4 Exemple pratique avec Docker Compose

Reprenons l’exemple Flask/Postgres pour voir Compose en action :

Imaginons que vous avez la structure de fichiers suivante pour votre projet :

```
mon-projet/
├── docker-compose.yml
├── Dockerfile         (pour le service web)
├── app.py             (application Flask)
├── requirements.txt   (dépendances Python)
```

**Exemple de Dockerfile (service web)** :
```Dockerfile
FROM python:3.10-slim
WORKDIR /app
# Install deps
COPY requirements.txt .
RUN pip install -r requirements.txt
# Copy app source
COPY . .
# Expose port (facultatif pour documentation, Flask utilise 5000 par défaut)
EXPOSE 5000
CMD ["python", "app.py"]
```
*(Ce Dockerfile prend un Python slim, installe Flask via requirements.txt, et lance app.py.)*

**docker-compose.yml** (comme vu plus haut) configure deux services: `web` (build local) et `db` (image Postgres). 

Étapes pour lancer l’application :
```bash
# 1. Assurez-vous d'être dans le dossier mon-projet/
docker-compose up -d  # démarre web + db en arrière-plan

# 2. Vérifiez que les conteneurs tournent
docker-compose ps    # doit montrer 2 conteneurs up (web_1, db_1)

# 3. Initialisation de la base (optionnel, selon app)
# Par ex, on pourrait avoir un script Flask pour créer les tables:
docker-compose exec web flask db init

# 4. Consulter les logs pour voir si tout se passe bien
docker-compose logs -f

# 5. L'application Flask devrait être accessible sur http://localhost:5000
```

Après tests :
```bash
# Arrêter et nettoyer quand fini
docker-compose down
```

Cet exemple montre la simplicité apportée par Compose : une seule commande `up` a créé le réseau par défaut, lancé Postgres et Flask. Flask a pu se connecter à Postgres en utilisant le nom de service `db`. Tout est encapsulé dans le dossier, versionnable, facile à partager avec un collègue (il n’a qu’à faire `docker-compose up` après avoir cloné le projet pour avoir le même environnement).

### 5.5 Orchestration de base avec Docker sans orchestrateur externe

Docker Compose orchestre sur **une seule machine**. Si vous avez besoin d’orchestrer sur plusieurs machines (cluster), on passe à Docker Swarm ou Kubernetes (qu’on verra en chapitre 9). Mais mentionnons rapidement une fonctionnalité intégrée de Docker Engine : le mode **Swarm**.

Docker Swarm (mode “swarmkit” intégré) vous permet de transformer plusieurs moteurs Docker en un cluster orchestré simplement avec Docker Engine, sans installer K8s. Compose peut d’ailleurs déployer un stack sur un Swarm avec `docker stack deploy`.

Pour l’instant, retenez que Compose est pour le single-node (ou une VM de dev), alors que d’autres orchestrateurs gèrent le multi-node.

### 5.6 Checklist – Docker Compose

- **✓ Fichier YAML valide** : Indentation cohérente, version de format précisée, services définis correctement.
- **✓ Services découpés logiquement** : Un service par rôle (app, db, cache, proxy...), nom clair, image ou build défini.
- **✓ Communication inter-services** : Utilisation de `depends_on` si nécessaire, variables d’env pointing vers les bons hostnames (noms de service).
- **✓ Volumes & ports déclarés** : Tout port d’accès extérieur listé sous `ports`, les volumes persistants nommés déclarés en top-level.
- **✓ Commandes Compose maîtrisées** : `up`, `down`, `logs`, `exec`, `ps`, `build`. Savoir reconstruire un service après modif, etc.
- **⚠️ Attention** : Ne pas lancer plusieurs `docker-compose up` de la même app sans les isoler (risque de conflit de ports/noms). Utilisez le paramètre `-p <projet>` pour définir un nom de projet si vous voulez avoir deux instances du même compose (par défaut le nom du dossier est pris). Aussi, veillez aux volumes nommés : si vous réutilisez un nom de volume d’une autre app, vous partagerez les données (peut être voulu ou non).

---

## 6. Optimisation et performance

Ce chapitre aborde les **bonnes pratiques pour optimiser les performances** de vos conteneurs et de Docker en général. Nous verrons comment améliorer les performances des images, des conteneurs au runtime, et comment surveiller les ressources utilisées (monitoring).

### 6.1 Optimisation des performances des images

La performance d’une image se mesure souvent en **taille** (impacts sur le temps de téléchargement, l’espace disque) et en **temps de build**. Voici des conseils pour optimiser cela :

- **Images plus petites = déploiements plus rapides** : Une image légère se transfert plus rapidement vers un serveur ou un autre environnement. Cela réduit le temps de déploiement et le temps de démarrage du conteneur (car moins de données à extraire). Donc reprenons l’idée déjà évoquée : base image minimaliste, nettoyage des fichiers temporaires, usage de multi-stage pour ne garder que l’essentiel.
- **Nombre de couches** : Techniquement, trop de couches peut légèrement ralentir la création de conteneur (chaque couche est un overlay à monter). Ce n’est généralement pas le facteur principal de perf, mais sachez que Docker a une limite (128 couches maximum). Combinez des RUN quand cela a du sens pour ne pas approcher cette limite.
- **Chargement lazy des données** : Docker télécharge les couches d’image en parallèle, mais charge réellement les données d’une couche dans un conteneur au fur et à mesure qu’elles sont accédées (copie sur écriture). Donc même une image de 1GB, si votre conteneur n’utilise qu’une partie des fichiers, ce n’est pas entièrement chargé en RAM. Toutefois, pour l’I/O disque et le stockage, la taille compte toujours.
- **Locality du contexte** : Lors de `docker build`, Docker envoie le contexte (dossier courant par défaut) au démon Docker. Si vous avez beaucoup de fichiers non exclus, ce transfert peut être long. D’où l’importance de `.dockerignore` pour la performance de build.
- **Construire sur un bon stockage** : Sur Windows/Mac, le démon Docker tourne dans une VM Linux. Utilisez des chemins de contexte sur l’espace dédié Docker pour plus de vitesse (par ex, sur macOS, le contexte Docker se situe dans la VM, builder depuis un bind mount Mac peut être plus lent).
- **Cache de build et CI** : Si vous faites des builds dans un pipeline CI, essayez de mettre en place un système de cache (par ex, GitLab CI peut utiliser le Docker daemon comme cache entre jobs, ou vous pouvez pousser/puller une image de cache). Un build sans cache à chaque fois est coûteux.

### 6.2 Optimisation de l’exécution des conteneurs

Lorsqu’un conteneur tourne, plusieurs éléments peuvent impacter ses performances (et celles du host) :

- **Limitation des ressources (CPU, RAM)** : Par défaut, un conteneur peut utiliser tout le CPU et la RAM disponibles sur l’hôte (pas de limite). En environnement multi-conteneurs, surtout en prod, il est prudent de définir des limites pour éviter qu’un conteneur glouton n’affecte les autres ou l’hôte.  
  - *CPU* : utilisez `--cpus` (ex: `--cpus="1.5"` pour 1.5 CPU) ou les options plus fines `--cpu-shares`, `--cpu-quota`.  
  - *RAM* : utilisez `-m` / `--memory` (ex: `--memory="500m"` pour 500 Mo). On peut aussi définir `--memory-swap` pour limiter le swap.
  - *Nombre de processus* : `--pids-limit` pour limiter le nombre de PID qu’un conteneur peut créer (éviter un fork bomb).
  
  Ces limites utilisent les cgroups du kernel. En fixant des limites raisonnables, vous **protégerez** votre hôte et aurez des perfs plus prévisibles. Par exemple, sur un serveur 8Go RAM, vous pouvez donner max 6Go à un conteneur de base de données, gardant 2Go pour le reste du système et Docker.
  
- **Affinity CPU** : Vous pouvez épingler un conteneur à certains cœurs CPU (`--cpuset-cpus="0,1"` pour ne prendre que CPU 0 et 1). C’est utile pour isoler des workloads spécifiques ou améliorer la cache locality sur CPU.
- **I/O disques** : Par défaut tous les conteneurs partagent l’I/O disque. On peut limiter le débit d’I/O (`--device-read-bps`, etc. pour assigner une QoS). Rarement utilisé en pratique sauf besoins spécifiques.
- **Performance réseau** : Sur de la haute charge réseau, surveillez l’overhead NAT du mode bridge. Dans certains cas extrêmes, `--network host` ou macvlan peuvent offrir de meilleures latences/throughput. Mais attention aux implications.
- **Binds vs volumes** : Sur Docker Desktop (Win/Mac), l’I/O des bind mounts (dossiers de l’host) est plus lente que l’I/O dans un volume. Si performance I/O critique en dev, envisagez de déplacer les données dans un volume Docker plutôt qu’un dossier monté depuis l’OS hôte. Sur Linux natif, ce problème est moindre.
- **Taille des conteneurs** : Un conteneur qui grossit beaucoup (par ex, qui écrit énormément de données sur son layer RW sans utiliser de volume) peut impacter les perfs (car le driver de stockage doit gérer un gros diff). Évitez d’écrire trop de données non persistées, ou committez-les en image si c’est nécessaire, ou mieux, externalisez sur volume.

### 6.3 Outils de monitoring et mesure des performances

Pour optimiser, il faut pouvoir mesurer. Docker propose des commandes et il existe des outils tiers :

- **docker stats** :  
  ```bash
  docker stats [conteneur...]
  ```  
  Montre en temps réel l’utilisation CPU, mémoire, I/O, réseau de vos conteneurs. C’est pratique pour un check rapide. Sans argument, montre tous les conteneurs actifs.
- **docker inspect** (stats) : L’API Docker permet de récupérer des stats JSON plus détaillées, mais pour débuter `docker stats` suffit.
- **cAdvisor** : Un outil de Google qui collecte les métriques détaillées de Docker (CPU, mémoire, filesystem par conteneur…) et expose ça sur une UI web. On peut le lancer en conteneur lui-même :
  ```bash
  docker run -d --name=cadvisor -p 8080:8080 \
    -v /var/run/docker.sock:/var/run/docker.sock:ro \
    -v /sys:/sys:ro \
    -v /var/lib/docker/:/var/lib/docker:ro \
    gcr.io/cadvisor/cadvisor:latest
  ```  
  Puis http://localhost:8080 offre un tableau de bord. (Il requiert l’accès au socket Docker et systèmes, donc usage plutôt en local ou sur serveurs de monitoring internes).
- **Intégration Prometheus/Grafana** : Pour de la supervision plus complète, on peut envoyer les métriques Docker dans Prometheus (via l’endpoint cAdvisor ou Node Exporter) et visualiser via Grafana. Ceci sort du scope d’une intro Docker, mais sachez que c’est faisable.
- **Logs et métriques applicatives** : N’oubliez pas de monitorer l’application elle-même (à l’intérieur). Docker ne remonte pas tout. Par exemple, pour une base de données containerisée, utilisez vos outils habituels (ex: PMM pour MySQL) pour surveiller les requêtes lentes, etc.
- **Profiling** : Si vous suspectez un souci de perf dans un container, ce sont les mêmes outils qu’habituellement (profiler de l’application, etc.) puisque c’est l’application qui consomme CPU/Memory. Docker n’ajoute pas tant d’overhead en lui-même (quelques % au plus).

### 6.4 Bonnes pratiques de performance

- **Dimensionner selon l’usage** : N’allouez pas toujours max de ressources par conteneur. Par exemple, une petite app web peut très bien tourner avec 256Mo de RAM, alors qu’une base de données aura besoin de plus. Ajustez `--memory` en conséquence en prod pour éviter le gaspillage ou l’asphyxie.
- **Éviter le swap/container** : Si un conteneur utilise plus de RAM que disponible, il va swapper (si swap autorisé). C’est souvent catastrophique en termes de performance pour des bases de données notamment. Il vaut mieux que le conteneur tue le process (Out-Of-Memory) que de swap interminablement. Donc éventuellement mettre `--memory-swap` égal à `--memory` pour dire “pas de swap, juste cette limite” si l’appli le supporte.
- **Baser plusieurs conteneurs sur la même image** : Si vous lancez plusieurs conteneurs de la même image sur une machine, ils partagent les couches en lecture seule en mémoire. Donc c’est efficace en termes d’usage de RAM. Préférer ça que de cloner une appli en créant 5 images différentes très similaires.
- **Mettre à jour Docker** : Les nouvelles versions améliorent parfois les performances du moteur (ex: nouveau drivers, meilleurs performances sur Windows WSL2 au fil du temps). Ne restez pas sur une version trop vieille.

### 6.5 Checklist – Optimisation

- **✓ Images épurées** : Pas de poids excessif, multi-stage appliqué, pas de fichiers inutiles embarqués.
- **✓ Ressources maîtrisées** : Limites CPU/RAM définies pour les conteneurs importants en contexte multi-services.
- **✓ Monitoring en place** : Utilisation de `docker stats` ou d’outils plus poussés pour vérifier la conso.
- **✓ Load testing** : (pour les pros) tests de charge effectués sur les conteneurs pour repérer les goulots (on teste comme on ferait hors Docker, plus overhead potentiels).
- **✓ Pas de mystère** : Si un conteneur ralentit, être capable de déterminer si c’est l’app à l’intérieur qui est lente ou un manque de ressources ou un contention (verrou, I/O). Docker n’est généralement pas la cause profonde.
- **⚠️ À éviter** : Laisser tourner trop de conteneurs sur un petit hôte sans surveillance (risque d’OOM ou d’épuiser CPU). Lancer un conteneur gourmand sur une machine déjà chargée en pensant qu’il restera "sagement" dans son coin – sans limites il peut prendre ce qui reste. Oublier l’impact du stockage : une image de 5GB sur 10 machines = 50GB d’espace utilisé, attention au nettoyage.

---

## 7. Sécurisation

La sécurité est un aspect crucial de Docker, tant pour les images que pour les conteneurs en cours d’exécution. Dans ce chapitre, nous abordons les **techniques de sécurisation des conteneurs et des images**, ainsi que les bonnes pratiques DevOps pour garder un environnement Docker sûr.

### 7.1 Sécurité des images Docker

**Images officielles et vérifiées :**  
Toujours **privilégier les images officielles ou de sources sûres**. Docker Hub propose des images “Official” (marquées avec un badge officiel) pour les logiciels courants (nginx, redis, ubuntu, etc.). Ces images sont maintenues par Docker ou l’éditeur du logiciel. Évitez d’utiliser une image inconnue postée par un tiers sans vérification (risque de malware, backdoor, crypto-miner...). Si vous utilisez des images tierces, lisez la description, le Dockerfile source, les commentaires.

**Mises à jour et vulnérabilités :**  
Les images contiennent souvent des systèmes (Ubuntu, Alpine, etc.) avec des paquets. **Maintenez à jour vos images** en les reconstruisant régulièrement à partir de bases à jour. Des failles (ex: OpenSSL, log4j, etc.) peuvent impacter des images Docker aussi. Docker ne patche rien automatiquement : c’est à vous de rebuild/pull des images plus récentes.  
Outils d’analyse de vulnérabilité d’images :
- *Docker Scan* (intégré via Snyk dans Docker Desktop) : vous pouvez lancer `docker scan image:tag` pour obtenir un rapport des CVE connues.
- *Trivy* (Aqua Security) : un scanner en ligne de commande gratuit qui inspecte images et Dockerfiles pour trouver des vulnérabilités et mauvaises pratiques.
- D’autres : Clair, Anchore, etc. pour intégration CI.

**Réduction de surface d’attaque :**  
- Utilisez des images minimalistes (on l’a assez répété 😅) – moins de packages = moins de vulnérabilités potentielles.
- N’ajoutez pas de credentials ou secrets en dur dans l’image. Par exemple, ne faites pas `RUN echo "DB_PASSWORD=secret" > /root/.env` – car même si c’est dans un layer précédent puis supprimé, le contenu peut rester accessible dans l’historique des couches.  
- Si vous avez besoin de secrets à build-time, utilisez des *build args* ou l’outil `docker buildx --secret` qui évite de les stocker en dur dans l’image. Mieux encore, injectez les secrets au runtime via des variables d’environnement ou volumes (voir section 7.3).
- **Signature d’images** : Docker offre la possibilité de signer les images (Docker Content Trust / Notary). Cela permet à un client Docker de vérifier qu’il tire une image non altérée provenant d’une source de confiance. Activez Docker Content Trust (variable env `DOCKER_CONTENT_TRUST=1`) si vous mettez en place la signature de vos images en entreprise, pour prévenir les attaques de type "falsification d’image".
- **Scan avant push** : Intégrez un scan de vulnérabilités dans votre pipeline CI avant de pousser une image en production. Mieux vaut détecter en amont qu’une image de base a un package avec faille.

### 7.2 Sécurité des conteneurs (runtime)

Même si les conteneurs offrent une isolation, ils partagent le noyau de l’hôte, donc **une compromission d’un conteneur peut affecter l’hôte** si on n’est pas vigilant. Voici les bonnes pratiques :

- **Ne pas exécuter en root (dans le conteneur)** : Par défaut, si vous ne spécifiez rien, le process dans le conteneur tourne en root *utilisateur root du conteneur*. Ce n’est pas idéal. Ajoutez un utilisateur non-privilégié dans votre Dockerfile (via `useradd` et `USER` comme vu au chapitre 4) ou utilisez les images qui prévoient un user (beaucoup d’images officielles ont un user par défaut, ex: `node` dans l’image Node, `nginx` dans nginx).  
  Pourquoi ? Si une faille permet de sortir du conteneur, si le process tournait en root, l’attaquant aura potentiellement root sur l’hôte. Si c’était un user restreint, l’impact est réduit.
- **Limiter les capacités Linux** : Docker, par défaut, limite certaines *capabilities* du conteneur (par exemple, pas de montage de FS, pas d’accès raw aux devices, etc.), mais l’utilisateur root du conteneur a encore beaucoup de pouvoirs (presque autant qu’un root sur un namespace isolé). On peut réduire davantage avec l’option `--cap-drop` pour enlever des capabilities, ou `--cap-add` pour en ajouter uniquement précises au lieu de tout donner par défaut. Par exemple, une application web n’a probablement pas besoin de la capacité NET_RAW (paquets raw) – on peut dropper `NET_RAW` pour réduire les possibilités d’attaque.
- **Mode read-only** : Pour renforcer la sécurité, on peut démarrer un conteneur en read-only sur son système de fichiers : `--read-only`. Couplé avec des volumes en écriture pour les répertoires qui ont *vraiment* besoin d’écrire (ex: /tmp, /var/log...). Ainsi, même si une attaque survient, l’attaquant ne peut pas altérer les fichiers système car tout est monté en lecture seule.
- **User Namespace** : Docker propose d’isoler les IDs utilisateurs du conteneur par rapport à l’hôte (user namespace remapping). En gros, le “root” à l’intérieur pourrait être mappé à un ID utilisateur non privilégié sur l’hôte. C’est un setup un peu avancé qu’on peut activer dans le démon Docker (`/etc/docker/daemon.json` avec `"userns-remap": "default"` par exemple). Cela ajoute une couche de sécurité, au prix de quelques complexités (partage de volumes entre conteneurs plus compliqué, etc.). À envisager pour des déploiements à risque élevé.
- **Pas de privilège total** : Évitez `--privileged` sauf cas ultra spécifiques. Cette option donne *tous* les droits au conteneur (accès à tous les devices, toutes les capabilities, etc.), ce qui équivaut quasiment à avoir une root full power sur l’hôte. La plupart du temps, ce n’est pas nécessaire.
- **Limiter les ressources = limiter l’impact** : Indirectement, définir des quotas CPU/RAM (voir chapitre 6) aide aussi la sécurité/disponibilité : un conteneur compromis (ex: cryptojacking) sera limité en conso, et ne rendra pas le système complètement inutilisable.
- **Expose minimal de ports** : N’exposez que les ports nécessaires. Chaque port exposé est une surface d’attaque potentielle si le service derrière a une vulnérabilité. Par exemple, inutile d’exposer l’interface d’admin d’une base de données sur Internet – laissez-la inaccessible ou sur un réseau interne.
- **Firewall/Network policy** : En complément, utilisez des règles de pare-feu (iptables, ufw) ou des *network policies* (si orchestrateur) pour contrôler quel conteneur peut parler à qui, spécialement si plusieurs applis sensibles cohabitent.
- **Audit et surveillance** : Surveillez vos conteneurs runtime. Par exemple, l’outil *Falco* (de Sysdig) peut surveiller en temps réel les comportements suspects (ex: un conteneur qui spawn un shell, qui touche /etc/passwd, etc.) et alerter.
- **Procfs et données sensibles** : Évitez de monter des sockets système ou des dossiers sensibles de l’hôte dans un conteneur. Un cas particulier est `/var/run/docker.sock` (le socket Docker de l’hôte). Si vous le montez dans un conteneur (pratique courante pour que le conteneur pilote Docker), sachez que ce conteneur a alors le contrôle total sur le daemon Docker (et donc sur l’hôte en entier). À ne faire que pour des conteneurs de confiance (ex: portainer, CI agent) et idéalement avec des mesures de sécurité supplémentaires.

### 7.3 Gestion des secrets et config

Ne mettez pas de mots de passe, clés privées ou secrets directement dans vos images ou en variables d’environnement en clair dans Compose (risque d’oubli, ou de leak via `docker inspect`). Préférez :

- **Fichiers de configuration externes** : Montez un fichier de config contenant le secret via un volume, ou utilisez les *secrets* Docker Swarm si en mode cluster (ils apparaissent en tmpfs dans le conteneur).
- **Variables d’environnement via fichiers** : Plutôt que d’écrire en dur dans compose, utilisez un fichier `.env` à côté du compose, que vous ne versionnez pas, et Compose va substituer dedans. Ou passez-les au moment du run.
- **Stores de secrets externes** : Pour les gros déploiements, intégrez un Vault (Hashicorp Vault, AWS Secrets Manager...) et codez votre appli pour qu’elle aille chercher ses secrets au démarrage au lieu de les recevoir statiquement.

### 7.4 Meilleures pratiques DevOps en sécurité Docker

En mode DevOps, intégrez la sécurité dès le début (DevSecOps) :

- **Analyse statique** : Utilisez des outils (Hadolint, Trivy, Snyk, etc.) dans votre pipeline CI pour analyser Dockerfile et image à chaque build. Si une nouvelle vulnérabilité critique est trouvée, échouez la pipeline pour éviter de déployer une image à risque.
- **Principle of least privilege** : N’accordez aux pipelines, utilisateurs, conteneurs que les droits dont ils ont besoin. Ex: si un pipeline CI doit déployer sur un serveur via Docker, donnez-lui un user qui peut juste pousser l’image et exécuter le conteneur, pas modifier la config Docker du serveur.
- **Mises à jour et patches** : Suivez les flux de sécurité des composants que vous utilisez. Par exemple, si vous déployez beaucoup de conteneurs Node.js, abonnez-vous aux news de sécurité Node pour reconstruire vos images ASAP quand une faille critique sort.
- **Isolation des environnements** : Séparez les environnements de conteneurs selon leur criticité. Ex: l’hôte Docker de prod n’est pas le même que celui de test (pour éviter qu’une compromission test permette d’aller en prod).
- **Registry privé sécurisé** : Si vous stockez des images sensibles sur un registre privé, assurez-vous qu’il est bien sécurisé (authentification, éventuellement tenu à jour lui aussi pour éviter qu’il soit vecteur d’attaque). Activez la signature d’images sur le registry si possible.
- **Docker Bench for Security** : Docker fournit un script (Docker Bench) qui check la configuration de votre daemon Docker et de l’OS pour comparer aux bonnes pratiques (ex: s’assurer que le démon n’écoute pas sur le réseau sans TLS, que le root du Docker host est verrouillé, etc.). Lancez-le de temps en temps sur vos serveurs Docker pour voir les points à améliorer.

### 7.5 Checklist – Sécurité

- **✓ Images de confiance** : Utilisation d’images officielles ou sources vérifiées. Scan régulier des images.
- **✓ Pas de secrets en dur** : Aucunes clés ou mdp dans les Dockerfile ou images finales. Secrets injectés au runtime de manière sécurisée.
- **✓ Process non-root** : Dans la mesure du possible, vos conteneurs tournent en utilisateur limité. Si un service requiert root (rare), l’isoler doublement.
- **✓ Ports & network maîtrisés** : Pas de ports exposés inutilement, conteneurs sensibles isolés sur des réseaux privés non accessibles publiquement.
- **✓ Durcissement** : Capabilities droppées pour les conteneurs simples, filesystem read-only si possible, `--privileged` banni sauf exception documentée.
- **✓ Surveillance** : Monitoring des conteneurs en place (métriques, comportements), plan de réponse en cas d’activité anormale.
- **⚠️ Points d’attention** : Ne pas oublier que la sécurité de Docker dépend aussi de la sécurité de l’hôte (gardez votre OS hôte à jour, pare-feu configuré, accès SSH restreint, etc.). Une mauvaise config de l’hôte = Docker vulnérable. Évitez d’exposer l’API Docker socket sans protection (par défaut elle est socket UNIX local, ne la passez pas en TCP ouvert). 

---

## 8. Intégration avec DevOps et CI/CD

Docker s’intègre parfaitement dans les workflows DevOps, en particulier les pipelines **CI/CD (Intégration Continue / Déploiement Continu)**. Dans ce chapitre, nous verrons comment utiliser Docker dans les pipelines, pour automatiser tests et déploiements, et comment Docker facilite la collaboration entre développement et opérations.

### 8.1 Docker dans les pipelines d’intégration continue (CI)

**Build d’image automatisé :**  
Un schéma courant est de **construire l’image Docker de votre application à chaque commit** (ou à chaque release) via votre outil CI (Jenkins, GitLab CI, GitHub Actions, Azure DevOps, etc.). Cela garantit que l’image est toujours à jour et permet de tester l’application dans le même environnement qui ira en production.

Exemple (pseudo-code d’une pipeline) :
- Étape 1 : Récupérer le code (git clone).
- Étape 2 : `docker build -t monapp:${CI_COMMIT_SHA} .` pour builder l’image avec un tag unique (SHA du commit ou numéro de version).
- Étape 3 : `docker run monapp:${CI_COMMIT_SHA} npm test` – Lancer les tests à l’intérieur d’un conteneur identique à l’image. Ainsi, si les tests passent dans l’image, on est confiant que l’image est bonne pour prod.
- Étape 4 : (optionnel) Pousser l’image vers un registre (Docker Hub, ECR, GitLab Registry…) avec un tag versionné ou `latest`.
- Étape 5 : Déclencher le déploiement en récupérant cette image.

Beaucoup d’outils CI ont un support natif de Docker :
- **GitLab CI** : Permet d’utiliser Docker DinD (Docker-in-Docker) ou le socket du runner pour builder et pousser des images. Exemple d’un job GitLab CI YAML:  
  ```yaml
  build_image:
    stage: build
    image: docker:20.10
    services:
      - docker:20.10-dind
    script:
      - docker login -u "$CI_REGISTRY_USER" -p "$CI_REGISTRY_PASSWORD" $CI_REGISTRY
      - docker build -t $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA .
      - docker push $CI_REGISTRY_IMAGE:$CI_COMMIT_SHA
  ```
  Ici on utilise l’image Docker officielle, plus un service dind (Docker en docker) pour pouvoir exécuter les commandes.
- **GitHub Actions** : Possède des actions préfaites comme `docker/build-push-action` pour builder et publier.  
- **Jenkins** : On peut utiliser un agent Docker ou le plugin Docker Pipeline. Par exemple, un Jenkinsfile qui fait `docker.build("monapp:${env.BUILD_NUMBER}")`.

**Tests multi-services en CI** :  
Grâce à Docker, on peut également lancer des services de test. Par exemple, si vous avez besoin d’une base de données pour les tests, vous pouvez, dans votre pipeline, lancer rapidement un conteneur de base de données (via `docker run -d postgres`), exécuter les tests de votre app qui se connecte dessus, puis supprimer le conteneur. C’est beaucoup plus simple que d’installer la DB sur l’agent CI lui-même.

Beaucoup de systèmes CI ont des **services éphémères** intégrés. Ex: GitHub Actions permet de définir des services (via docker) qui seront dispo durant le job (une base, un redis, etc.). GitLab CI permet de définir des services Docker par job aussi.

**Cache Docker en CI** :  
Pour éviter de retélécharger les mêmes couches à chaque build, mettez en place un cache :
- Soit un registre intermédiaire : par ex, puller `monapp:latest` avant de build pour que Docker réutilise les couches communes.
- Soit utiliser la cache du runner si possible (GitLab Runner en mode docker peut monter /var/lib/docker en cache).
- Utiliser les outils comme BuildKit qui peuvent pousser/puller des caches de layers séparément.

### 8.2 Docker pour le déploiement continu (CD)

Une fois que l’image Docker est prête et testée, le déploiement continu consiste à la déployer en environnement (staging, prod).

**Registry comme point central :**  
L’image Docker construite devient l’artifact de déploiement. Elle est stockée dans un registry accessible depuis les serveurs de prod. Par exemple, vous poussez `mon-registry.internal/app:1.2.3`. Sur vos serveurs, le pipeline de déploiement exécutera `docker pull mon-registry.internal/app:1.2.3` puis `docker run ... app:1.2.3` (ou via orchestrateur). Cela simplifie l’artifact management : plus besoin de transférer un zip de code, de configurer l’environnement – tout est dans l’image.

**Orchestration du déploiement :**  
- Pour déployer *sur une VM classique* : le pipeline peut se connecter en SSH et lancer le conteneur (ou mettre à jour un compose file et faire `docker-compose up -d`).
- Mieux, si vous utilisez un orchestrateur (Swarm, Kubernetes), le pipeline interagit avec celui-ci (ex: `docker stack deploy` pour un Swarm, ou `kubectl apply` pour Kubernetes, voir chapitre 9).
- On peut aussi utiliser des outils comme Portainer, Watchtower ou autres qui surveillent un registre et mettent à jour les conteneurs quand une nouvelle image est disponible.

**Rollbacks faciles :**  
Avec Docker, revenir à une version précédente est aisé : il suffit de relancer le conteneur avec l’ancienne image taggée. D’où l’importance de tagger les versions (ne déployez pas juste “latest” partout; si une image latest pose problème, latest-1 n’existe pas vraiment, il faut un tag immuable comme un n° de version ou commit SHA).

**Environnements homogènes :**  
CD avec Docker facilite d’avoir le *même container en staging et en prod*. On élimine les "ça marchait en staging mais pas en prod parce que config/env diffère". Si besoin de différences de config, utilisez les variables d’environnement ou fichiers de config montés, gérés par l’orchestrateur ou Compose via des fichiers `.env` différents.

### 8.3 Collaboration DevOps améliorée

Docker joue un rôle de liant entre Dev & Ops :
- Les devs écrivent le Dockerfile et docker-compose pour leur app. Ce même Dockerfile sert à Ops pour la construire en prod. Fini les "works on my machine" : tout est codifié.
- Les ops peuvent demander aux dev d’ajouter des *healthchecks* (via l’instruction `HEALTHCHECK` dans Dockerfile) pour que l’orchestrateur puisse savoir si l’app est saine. Ou de prévoir des variables pour paramétrer l’image selon l’environnement.
- La CI/CD orchestrée autour de Docker signifie que tout le monde parle le même langage : "quelle image tourne ? quelle version d’image déployée ?".
- **Immutable infrastructure** : DevOps prône souvent l’infrastructure immutable (on ne patch pas en live un serveur, on redéploie une nouvelle instance à jour). Docker facilite cela en permettant de re-créer conteneur et de supprimer l’ancien au lieu de faire des mises à jour hasardeuses sur un conteneur existant. C’est le principe du *phoenix server* vs *snowflake server*.

### 8.4 Exemples concrets d’intégration

- **Exemple 1 (GitHub Actions)** : Une application Node.js:
  - Dev écrit un Dockerfile.
  - GitHub Actions sur push main:  
    - Build l’image, taggée `myapp:$GITHUB_SHA` et `myapp:latest`.  
    - Lance `docker run myapp:$GITHUB_SHA npm test`.  
    - Push sur Docker Hub.
    - Déploie sur un serveur via SSH en pullant l’image.
- **Exemple 2 (GitLab)** : Microservice Java + Compose:
  - Dev a un docker-compose pour dev (avec DB).
  - CI GitLab build le jar, construit une image, push sur GitLab Registry avec tag de commit.  
  - CI déploie sur un Swarm cluster via `docker stack deploy -c docker-compose.prod.yml myapp` (ici on utilise le même format Compose mais en mode Swarm, possible car GitLab Runner peut accéder au docker remote).
- **Exemple 3 (Jenkins + Kubernetes)** :
  - Jenkins pipeline construit l’image, la pousse.
  - Pipeline mise à jour un manifest Kubernetes (fichier .yaml déployé via `kubectl`) pour pointer vers la nouvelle image tag.
  - Applique le manifest. Kubernetes se charge de tourner en rolling update (progressivement remplacer les conteneurs par la nouvelle image).

### 8.5 Checklist – CI/CD Docker

- **✓ Dockerfile inclut tests** : Optionnel mais on peut inclure des tests ou un mode test (ou simplement utiliser l’image pour tests) dans la CI.
- **✓ Pipeline CI configuré** : Accès au daemon Docker (DinD ou hôte) sécurisé, credentials pour push (ne jamais mettre en clair, stocker dans vault/secret de la CI).
- **✓ Artifact = image** : Pipeline produit une image immuable, testée, prête à déployer. Pas de configuration manuelle après coup sur le serveur.
- **✓ Tags et versioning** : Image taggée avec version unique (commit, date, semver), `latest` utilisé prudemment ou pour dev uniquement.
- **✓ Déploiement automatique** : Pipeline CD prend l’image et la déploie via l’outil approprié (SSH script, docker-compose, CLI orchestrateur). Monitoring post-déploiement (vérifier conteneur up, healthcheck OK).
- **⚠️ Points de vigilance** : Nettoyage des images dans le registre (ne pas garder 500 images si vous déployez à chaque commit, faites de la rétention), sécurité du daemon Docker dans le CI (le Docker dind exposé doit être isolé car en gros accès root), gérer les secrets d’ENV différemment entre dev/staging/prod (ne pas push une image contenant le config de prod par erreur).

---

## 9. Introduction à Kubernetes et Docker Swarm

Docker a popularisé les conteneurs, mais quand il s’agit de déployer et gérer des conteneurs à grande échelle (sur de multiples machines, avec haute dispo, etc.), on fait appel à des orchestrateurs tels que **Kubernetes** ou **Docker Swarm**. Ce chapitre offre une introduction à Kubernetes et mentionne Docker Swarm, en expliquant comment ils s’articulent autour de Docker et quelles sont les alternatives d’orchestration.

### 9.1 Pourquoi un orchestrateur ?

Avec 3-4 conteneurs, Docker Compose suffit. Mais imaginez devoir gérer **des dizaines ou centaines de conteneurs sur plusieurs serveurs** :
- Besoin de tolérance aux pannes (si un serveur tombe, les conteneurs doivent être relancés ailleurs).
- Mise à l’échelle dynamique (ajouter 5 instances de tel service car la charge augmente, puis les retirer).
- Mises à jour sans coupure (rolling updates).
- Service discovery (trouver où sont les conteneurs).
- Load balancing, etc.

Un orchestrateur est un outil/plateforme qui automatise tout cela. L’orchestrateur prend vos *descriptions d’applications* (souvent en YAML, comme Compose mais plus riche) et se charge de les maintenir en état désiré.

### 9.2 Kubernetes en bref

**Kubernetes (K8s)** est l’orchestrateur de conteneurs le plus utilisé actuellement. Initialement développé par Google (inspiré de son système interne Borg), c’est un projet open-source devenu la référence.

Concepts de base de Kubernetes :
- **Cluster** : un ensemble de machines (VMs, serveurs, ou même mini cluster sur votre PC) sur lesquelles K8s déploie les conteneurs. Un cluster a un *control plane* (cerveau, souvent plusieurs noeuds pour la redondance) et des *nodes* (ou *workers*, qui exécutent les conteneurs).
- **Pod** : l’unité de base de K8s. Un Pod encapsule un ou plusieurs conteneurs Docker (généralement 1 principal + conteneurs sidecar). Le Pod est l’unité de déploiement (si un Pod meurt, K8s le remplace, etc.). Les conteneurs d’un Pod partagent le même réseau (localhost commun) et système de fichiers temporaire.
- **Deployment** : un objet K8s qui décrit un ensemble de Pods identiques (par exemple "je veux 5 pods de mon app web"). Le Deployment gère la mise à l’échelle et les mises à jour (rolling update, rollback...).
- **Service** : un objet qui expose un ensemble de pods sur le réseau (interne ou externe) et fait du load-balancing. Par exemple, un Service "web-service" peut pointer vers les 5 pods de l’app web, et fournir une IP stable ou un DNS stable, ainsi que l’équilibrage de charge entre pods.
- **Ingress** : (optionnel) un composant pour la gestion fine du trafic entrant HTTP (par ex, router du trafic vers différents services en fonction de l’URL).
- **ConfigMap & Secret** : objets pour injecter de la configuration dans les conteneurs (fichiers de config ou variables) de façon externe au conteneur (pour ne pas les embarquer dans l’image).
- **Volume (PersistentVolume)** : K8s gère aussi les volumes, par le biais de PersistentVolumes/PersistentVolumeClaims qui abstraient le stockage (NFS, disque cloud, etc.) à monter dans les pods.

**Comment Kubernetes utilise Docker ?**  
Jusqu’il y a peu, Kubernetes s’appuyait sur Docker comme moteur pour lancer les conteneurs sur chaque node, via une couche appelée Docker Shim. Cependant, Docker en tant que tel n’est plus requis : K8s utilise désormais souvent **containerd** (le runtime underlying de Docker) ou d’autres runtimes conformes à l’interface CRI (Container Runtime Interface). Autrement dit, on peut faire tourner Kubernetes sans Docker, mais en pratique la plupart des images Docker fonctionneront identiquement car containerd exécute la même chose.  
Pour le développeur, on continue de créer des images Docker et de les pousser sur un registre. Kubernetes les tirera puis les lancera dans des conteneurs.

**Kubernetes en pratique** :
- Il faut déployer un cluster (par exemple avec Minikube pour tester en local, ou via un cloud (GKE, EKS, AKS), ou des outils comme kubeadm).
- On interagit avec le cluster via la CLI `kubectl` et des manifestes YAML.
- Exemple simplifié :  
  ```bash
  kubectl create deployment web --image=nginx
  kubectl scale deployment web --replicas=3
  kubectl expose deployment web --port=80 --type=LoadBalancer
  ```  
  Cela créerait un Deployment nommé "web" avec image Nginx, le scale à 3 pods, et expose un Service type LB pour y accéder.
- En vrai on écrit plutôt des fichiers YAML comme :  
  ```yaml
  apiVersion: apps/v1
  kind: Deployment
  metadata: { name: web }
  spec:
    replicas: 3
    selector: { matchLabels: { app: web } }
    template:
      metadata: { labels: { app: web } }
      spec:
        containers:
        - name: nginx
          image: nginx:latest
          ports: [{ containerPort: 80 }]
  ```  
  puis `kubectl apply -f deployment.yaml`.

Kubernetes est **complexe** à maîtriser entièrement, mais très puissant et modulable (système d’extensions opérateurs, etc.). Pour une intro Docker, retenez que K8s est l’étape suivante quand une appli Docker doit passer en production à grande échelle ou nécessiter de l’auto-réparation et du multi-node par défaut.

### 9.3 Docker Swarm

**Docker Swarm** est l’orchestrateur "maison" de Docker, intégré dans Docker Engine. On l’active en un simple `docker swarm init`. Il permet de grouper plusieurs hôtes Docker en un cluster Swarm et de déployer des stacks (définies en YAML proche de Compose v3).

Points clés de Swarm :
- **Services** : Equivalent des Deployments, on définit un service (image + nombre de replicas, ports, etc.) que Swarm va maintenir.
- **Overlay network** : Swarm crée des réseaux overlay automatiquement entre les hôtes pour que les conteneurs de service communiquent.
- **Simplicité** : Tout se fait via la commande Docker familière. Ex: `docker service create --replicas 3 -p 80:80 nginx` déploie un service Nginx en 3 exemplaires sur le cluster.
- **Stacks** : On peut utiliser un fichier Compose (avec `deploy` section) et faire `docker stack deploy -c compose.yml monstack`. Swarm va créer les services, volumes, réseaux décrits, sur tout le cluster.
- **High availability** : On peut avoir plusieurs managers (control plane) pour tolérer la panne d’un manager.
- **Secrets** : Swarm a une fonction de secrets intégrée aussi (on peut créer un secret et le monter en fichier dans les services).

Swarm est plus facile à prendre en main que Kubernetes, mais est moins riche en fonctionnalités/ecosystème. Il a l’avantage d’être inclus, sans dépendance externe. Il a été très utilisé, mais depuis la domination de K8s, son écosystème stagne un peu. Cela dit, pour une petite infra ou pour sa simplicité, il reste pertinent.

### 9.4 Autres alternatives d’orchestration

- **Nomad** (HashiCorp) : Orchestrateur agnostique (pas que Docker, aussi des exécutables). Plus simple que K8s, très léger agent Go, mais moins répandu.
- **Docker Compose + outil de déploiement** : Certains choisissent de ne pas aller vers un orchestrateur full fledged, et continuent avec Compose en prod, orchestré par du scripting (par ex Ansible qui distribue un compose file et lance sur plusieurs hosts). Pas aussi robuste qu’un orchestrateur, mais pour quelques serveurs fixes, ça marche.
- **Serverless / PaaS** : Plutôt que gérer l’orchestration, des plateformes type Heroku, AWS ECS/Fargate, etc. peuvent prendre une image Docker et la déployer sans que vous gériez un cluster. C’est une sorte d’orchestration managée.
- **LXC/LXD** : Alternative de conteneurs système (Linux Containers par Canonical), plus orienté VM légères que microservices. Moins courant pour du déploiement app.

### 9.5 Quand utiliser Kubernetes vs Swarm vs autres ?

- **Kubernetes** : Choix par défaut pour de grands déploiements, microservices en production à l’échelle, besoin de fonctionnalités avancées (autoscaling, opérateurs, etc.), et si l’équipe est prête à investir dans la courbe d’apprentissage. Aussi, l’écosystème autour (monitoring, service mesh, CI/CD integration) est très riche.
- **Docker Swarm** : Si vous avez déjà Docker et que vous voulez orchestrer quelques machines sans trop de complexité. Déploiement rapide, la syntaxe Compose que vous connaissez peut être réutilisée. Mais moins de communauté/évolution.
- **Aucun orchestrateur** : Pour de toutes petites stacks (une appli monolithique par exemple), ou en phase de prototypage, il est possible que Docker Compose sur un serveur unique suffise. On peut vivre sans orchestrateur tant que la charge est modérée et qu’on a pas besoin de haute dispo auto (si le serveur tombe, tout tombe).
- **Nomad/Autres** : Si vous avez des besoins spécifiques ou déjà l’écosystème HashiCorp (Consul, Vault…), Nomad s’intègre bien. 

En somme, Kubernetes est la tendance actuelle pour la production, mais assurez-vous d’en avoir le besoin car cela ajoute de la complexité.

### 9.6 Checklist – Orchestration

- **✓ Compréhension des limites de Docker standalone** : On sait qu’au-delà d’une machine, il faut un orchestrateur pour le scheduling, failover, etc.
- **✓ Notions de base K8s** : Pod, Deployment, Service, Ingress, etc. au moins conceptuellement compris.
- **✓ Expérimenté localement** : Avoir au moins testé un Minikube ou un kind (K8s in Docker) pour déployer un hello-world, et/ou `docker swarm init` pour voir comment Swarm fonctionne.
- **✓ Choix pour mon projet** : Évaluer quel niveau d’orchestration est nécessaire (pas la peine de sortir K8s pour 2 conteneurs; inversement, ne pas sous-estimer la gestion manuelle si on a 50 conteneurs sur 5 VMs…).
- **✓ Outils complémentaires** : Savoir qu’en passants sur K8s, il faudra aussi prévoir des outils de logging (EFK), monitoring (Prometheus/Grafana), etc., ce qui peut être géré par des *Operators* ou Helm charts.
- **⚠️ Erreurs à éviter** : Penser que Docker en lui-même gère la haute dispo (non, il restart conteneur localement s’ils plantent si `--restart` mis, mais ne déplace pas ailleurs, etc.). Négliger la complexité de K8s – ça peut vite devenir ingérable sans expertise, donc ne pas foncer dedans sans formation/phase test. Swarm plus simple mais attention aux volumes/stockage (tout ce qui est stateful doit être pensé, ex: volumes NFS communs ou autres).

---

## 10. Checklists et résumés pratiques

Pour conclure ce guide, voici des **checklists récapitulatives** et des **meilleures pratiques** globales pour Docker. Ces listes peuvent servir de référence rapide pour éviter les erreurs courantes et s’assurer de suivre les bonnes pratiques lors de l’utilisation de Docker.

### 10.1 Checklist générale de bonnes pratiques Docker

- **Images & Dockerfile :**  
  - [ ] Utiliser des images de base minimalistes et officielles de préférence.  
  - [ ] Tenir les Dockerfile simples et lisibles, commenter les étapes importantes.  
  - [ ] .dockerignore configuré pour éviter d’envoyer des fichiers inutiles au build.  
  - [ ] Pas de secrets ou infos sensibles dans l’image (commits, layers).
  - [ ] Mettre à jour régulièrement les images de base et libérer les anciennes vulnérables.
  - [ ] Tester l’image localement avant de la pousser (ex: démarrer le conteneur et vérifier qu’il fonctionne comme attendu).
  - [ ] Utiliser des tags de version explicites pour traquer les déploiements (pas seulement "latest").

- **Conteneurs (exécution) :**  
  - [ ] Ne lancer qu’un seul processus principal par conteneur (le cas échéant, utiliser supervisord ou autre, mais c’est souvent un design à éviter).  
  - [ ] Utiliser `--name` pour nommer les conteneurs critiques, afin de les reconnaître facilement.  
  - [ ] Planifier la gestion des logs (les consulter, les stocker ou les rediriger hors conteneur si trop volumineux).  
  - [ ] Exposer uniquement les ports nécessaires, avec les bons mappings (et protégé par firewall si besoin pour éviter accès ext).  
  - [ ] Utiliser `--restart` policy en prod pour les conteneurs qui doivent tourner en continu (unless-stopped ou always).
  - [ ] Nettoyer régulièrement les conteneurs stoppés inutiles (`docker rm`) et les anciennes images (`docker rmi`) pour libérer de l’espace.
  - [ ] Surveiller l’utilisation ressource des conteneurs (via `docker stats` ou autre) pour ajuster si un conteneur consomme trop ou est sous-dimensionné.

- **Volumes & Données :**  
  - [ ] Toujours monter un volume pour les données critiques (BDD, fichiers uploads, etc.) – ne pas laisser ces données seulement dans le conteneur.  
  - [ ] Documenter où sont les volumes et ce qu’ils contiennent, pour faciliter sauvegardes/restauration/migration.  
  - [ ] Ne pas exposer de volumes sensibles à l’extérieur inutilement (ex: ne pas binder un volume contenant des secrets sur un répertoire host non sécurisé).  
  - [ ] Vérifier les permissions sur les volumes (l’utilisateur dans le conteneur doit avoir les droits nécessaires sur les fichiers montés).
  - [ ] Utiliser des volumes distincts pour séparer les types de données (ex: config vs data vs logs) si besoin d’un traitement particulier sur l’un d’eux.

- **Réseaux :**  
  - [ ] Organiser les conteneurs en réseaux isolés par application ou par rôle, pour limiter la portée de communication.  
  - [ ] S’assurer que les règles de firewall de l’hôte n’autorisent que le nécessaire sur les ports publiés.  
  - [ ] Tester la connectivité inter-conteneurs (ex: `docker exec` ping ou nc sur le port) pour valider que les links/réseaux fonctionnent comme voulu.  
  - [ ] Pour les conteneurs devant absolument avoir une IP accessible, envisager macvlan ou host network (en comprenant les implications).

- **Sécurité :**  
  - [ ] Vérifier les images (scan vulnérabilité) avant utilisation en prod.  
  - [ ] Ne pas utiliser `:latest` en prod sans contrôle (vous ne maîtrisez pas ce qui peut changer dans l’image).  
  - [ ] Les conteneurs tournent en user non root quand c’est possible (vérifier dans Dockerfile ou via option `--user`).  
  - [ ] Pas de `--privileged` ni de montage de socket Docker dans les conteneurs d’app (sauf besoin spécifique et mesuré).  
  - [ ] Mettre à jour Docker lui-même régulièrement pour bénéficier des patches de sécurité (démon Docker et Docker Compose s’il est séparé).  
  - [ ] Restreindre l’accès au daemon Docker (ne pas laisser n’importe qui exécuter docker sur le host, ni exposer l’API sans auth).  
  - [ ] Sauvegarder les données des volumes et éventuellement les images construites (registry mirror) en cas de besoin de reprise.

### 10.2 Erreurs courantes à éviter (Docker anti-patterns)

- **Conteneur trop gros, faisant trop de choses** : par exemple un conteneur qui lance une base de données + une appli + un cron... Découpez en plusieurs conteneurs ou services.
- **Ignorer les codes de sortie** : Si un `docker run` échoue (ex: port déjà pris), ne pas juste forcer `--restart=always` et oublier – corrigez la cause (libérer le port, etc.) plutôt que d’avoir un conteneur qui boucle.
- **Volume non monté en prod** : Tester en dev sans volume (donc l’app crée des fichiers en local), puis déployer en prod sans penser à monter un volume => perte de données à la recréation du conteneur. Toujours penser "stateless sauf volumes".
- **Mauvais mapping de ports** : Oublier le mapping ou inverser (ex: `-p 80:8080` vs `-p 8080:80` confusion) – résultat, soit pas accessible, soit pas le bon service exposé.
- **Confondre images et conteneurs** : Tenter de "modifier" une image en pensant que cela persiste dans le conteneur. Par ex, entrer dans un conteneur, installer un truc, et croire que l’image est modifiée – non, cela ne modifie que ce conteneur. Pour changer l’image, il faut reconstruire via Dockerfile ou commit l’image (ce dernier n’est pas recommandé hors debug).
- **Ne pas surveiller l’espace disque** : Docker peut consommer beaucoup d’espace (images, volumes, logs). Enchaîner les builds/images sans cleanup peut remplir un disque rapidement. Monitorer `/var/lib/docker` ou utiliser `docker system df` régulièrement.
- **Lancer docker en root sur serveur sans réfléchir** : Si vous donnez accès docker à un user, ce user peut obtenir root sur l’hôte (car docker run -v /:/host alpine rm -rf /host par exemple, c’est équivalent root). Donc, docker = root-like, d’où restriction d’accès.
- **Supposer que le conteneur est une boîte noire totalement isolée** : Il y a isolation, mais pas totale comme une VM. Le kernel est partagé, donc certaines configs sysctl ou param sys peuvent affecter l’hôte. Soyez conscient que c’est du "partage de noyau isolé".

### 10.3 Ressources recommandées

*(Une courte liste de ressources pour approfondir, en anglais pour la plupart car la doc officielle et communauté sont souvent anglophones)*

- Documentation officielle Docker : <https://docs.docker.com/> (Sections *Get Started*, *Engine*, *Compose*, etc. très complètes, avec tutoriels pas à pas).
- Play With Docker (PWD) : un site pour pratiquer Docker en ligne dans un environnement temporaire : <https://labs.play-with-docker.com/>
- Awesome Docker (GitHub) : une liste massive de ressources Docker (tutos, outils, images utiles) : <https://github.com/veggiemonk/awesome-docker>
- Docker Captains (blogs) : Les Docker Captains sont des experts reconnus, beaucoup tiennent des blogs avec des articles avancés (ex: Julien Simon, Nicolas De loof, Bret Fisher).
- Tutoriels Kubernetes (si vous allez plus loin dans l’orchestration) : <https://kubernetes.io/fr/docs/tutorials/>
- Outils à explorer : **Portainer** (UI de gestion Docker), **Watchtower** (mise à jour auto des images), **Dive** (analyse interactive de la taille des images couche par couche), **Hadolint** (linter Dockerfile).

### 10.4 Mots de la fin

Docker est un outil puissant qui, bien utilisé, apporte énormément en productivité et en fiabilité des déploiements. Ce guide vous a présenté un parcours du débutant à l’expert, couvrant l’installation, les concepts de base jusqu’aux sujets avancés de performance, sécurité, CI/CD et orchestration. 

En résumé, prenez le temps de maîtriser les bases (images, conteneurs, volumes, réseaux) avant de sauter dans l’avancé. Expérimentez, cassez des choses dans un environnement de test pour apprendre à les réparer. Docker a une communauté très active – n’hésitez pas à chercher de l’aide sur les forums, Stack Overflow ou la communauté Docker.

**Bonne conteneurisation !** Containerisez intelligemment, automatisez ce qui peut l’être, et gardez toujours un œil sur la sécurité et la maintenance de vos environnements. Docker n’est pas une fin en soi, mais un moyen d’atteindre des déploiements plus souples, cohérents et rapides. Profitez-en pour innover et accélérer vos workflows DevOps. Bon voyage dans l’univers de Docker 🚢🐳!