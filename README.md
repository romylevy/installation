# Installation de l'Environnement de Développement Python

## 01. Configuration suite de l'Installation d'Ubuntu

Ces actions ne sont nécessaires qu'une seule fois, après une installation (ou ré-installation) de l'OS sur la machine.

La version installée d'Ubuntu est la `22.04.3 LTS (Jammy Jellyfish)` et elle intègre un interpréteur Python `Python 3.10.12`.

- Pour afficher la version d'Ubuntu :
``` bash
cat /etc/os-release
```
ce qui donne :

```bash
PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy
```

- Pour afficher la version de Python :
``` bash
python3 --version
```

La version s'affiche :
```bash
Python 3.10.12
```

### Création du lien symbolique `python`

L'accès à l'interpréteur Python se fait avec la commnde `python3`.  Afin d'y accéder avec la commande plus simple `python`, il faut créer un lien symbolique entre la commande existante `python3` et la nouvelle commande `python`.

Pour cela, exécuter :
```
sudo ln -s /usr/bin/python3 /usr/bin/python
```

Comme la création de la commande `python` se fait dans le répertoire système protégé `/usr/bin`, il faut exécuter cette commande en tant que ***super utilisateur*** grâce à la commande `sudo`.

Cela signifie qu'à l'installation d'Ubuntu, votre compte utilisateur a été configuré pour avoir les droits de super utilisateur. L'utilisation de la commande `sudo` nécessite la vérification de votre identité et la saisie de votre mot de passe.

### Installation du module `venv`

Il existe de nombreuses versions de Python (`2.7`, `3.9`, `3.10`,...), chacune nécessitant des versions de librairies externes bien distinctes. Afin que ces différentes versions n'interfèrent pas les unes avec les autres, il est recommandé de cloisonner chaque projet Python dans un **environnement virtuel**.

Un **environnement virtuel** est un dossier auto-suffisant qui contient une installation d'une version particulière de Python ainsi que des paquets (ou librairies) additionnels.

Python permet de créer un environnement virtuel à l'aide du module `venv`. 

1. Pour installer le module `venv` pour la version de Python `3.10`, entrez la commande :

```bash
sudo apt install python3.10-venv
```

2. Vous verez apparaitre les logs :

```bash
[sudo] Mot de passe de romy : 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Les paquets supplémentaires suivants seront installés : 
  python3-distutils python3-pip-whl python3-setuptools-whl
Les NOUVEAUX paquets suivants seront installés :
  python3-distutils python3-pip-whl python3-setuptools-whl python3.10-venv
0 mis à jour, 4 nouvellement installés, 0 à enlever et 79 non mis à jour.
Il est nécessaire de prendre 2 612 ko dans les archives.
Après cette opération, 3 657 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer ? [O/n] o
Réception de :1 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 python3-distutils all 3.10.8-1~22.04 [139 kB]
Réception de :2 http://fr.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3-pip-whl all 22.0.2+dfsg-1ubuntu0.3 [1 679 kB]
Réception de :3 http://fr.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3-setuptools-whl all 59.6.0-1.2ubuntu0.22.04.1 [788 kB]
Réception de :4 http://fr.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3.10-venv amd64 3.10.12-1~22.04.2 [5 724 B]
2 612 ko réceptionnés en 0s (12,9 Mo/s)         
Sélection du paquet python3-distutils précédemment désélectionné.
(Lecture de la base de données... 204045 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../python3-distutils_3.10.8-1~22.04_all.deb ...
Dépaquetage de python3-distutils (3.10.8-1~22.04) ...
Sélection du paquet python3-pip-whl précédemment désélectionné.
Préparation du dépaquetage de .../python3-pip-whl_22.0.2+dfsg-1ubuntu0.3_all.deb ...
Dépaquetage de python3-pip-whl (22.0.2+dfsg-1ubuntu0.3) ...
Sélection du paquet python3-setuptools-whl précédemment désélectionné.
Préparation du dépaquetage de .../python3-setuptools-whl_59.6.0-1.2ubuntu0.22.04.1_all.deb ...
Dépaquetage de python3-setuptools-whl (59.6.0-1.2ubuntu0.22.04.1) ...
Sélection du paquet python3.10-venv précédemment désélectionné.
Préparation du dépaquetage de .../python3.10-venv_3.10.12-1~22.04.2_amd64.deb ...
Dépaquetage de python3.10-venv (3.10.12-1~22.04.2) ...
Paramétrage de python3-distutils (3.10.8-1~22.04) ...
Paramétrage de python3-setuptools-whl (59.6.0-1.2ubuntu0.22.04.1) ...
Paramétrage de python3-pip-whl (22.0.2+dfsg-1ubuntu0.3) ...
Paramétrage de python3.10-venv (3.10.12-1~22.04.2) ...
```

### Installation de Git

**Git** est un gestionnaire de version aussi appelé gestionnaire de source. Il permet de garder les traces de chaque modification de code et d'envoyer dans un dépôt distant son travail afin qu'il soit sauvegardé et puisse être partagé.

1. Pour l'installer :

```bash
sudo apt-get update
sudo apt-get install git
```

Les logs suivants s'affichent :

```bash
$ sudo apt-get update
sudo apt-get install git
[sudo] Mot de passe de romy : 
Atteint :1 http://fr.archive.ubuntu.com/ubuntu jammy InRelease
Atteint :2 http://fr.archive.ubuntu.com/ubuntu jammy-updates InRelease
Atteint :3 http://fr.archive.ubuntu.com/ubuntu jammy-backports InRelease
Atteint :4 https://dl.google.com/linux/chrome/deb stable InRelease
Atteint :5 http://security.ubuntu.com/ubuntu jammy-security InRelease
Lecture des listes de paquets... Fait                     
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Les paquets supplémentaires suivants seront installés : 
  git-man liberror-perl
Paquets suggérés :
  git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui gitk gitweb git-cvs git-mediawiki git-svn
Les NOUVEAUX paquets suivants seront installés :
  git git-man liberror-perl
0 mis à jour, 3 nouvellement installés, 0 à enlever et 2 non mis à jour.
Il est nécessaire de prendre 4 147 ko dans les archives.
Après cette opération, 21,0 Mo d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer ? [O/n] O
Réception de :1 http://fr.archive.ubuntu.com/ubuntu jammy/main amd64 liberror-perl all 0.17029-1 [26,5 kB]
Réception de :2 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.10 [954 kB]
Réception de :3 http://fr.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.10 [3 166 kB]
4 147 ko réceptionnés en 0s (20,6 Mo/s)
Sélection du paquet liberror-perl précédemment désélectionné.
(Lecture de la base de données... 204341 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../liberror-perl_0.17029-1_all.deb ...
Dépaquetage de liberror-perl (0.17029-1) ...
Sélection du paquet git-man précédemment désélectionné.
Préparation du dépaquetage de .../git-man_1%3a2.34.1-1ubuntu1.10_all.deb ...
Dépaquetage de git-man (1:2.34.1-1ubuntu1.10) ...
Sélection du paquet git précédemment désélectionné.
Préparation du dépaquetage de .../git_1%3a2.34.1-1ubuntu1.10_amd64.deb ...
Dépaquetage de git (1:2.34.1-1ubuntu1.10) ...
Paramétrage de liberror-perl (0.17029-1) ...
Paramétrage de git-man (1:2.34.1-1ubuntu1.10) ...
Paramétrage de git (1:2.34.1-1ubuntu1.10) ...
Traitement des actions différées (« triggers ») pour man-db (2.10.2-1) ...
```

2. Vérifions que son installation s'est bien déroulée :

```bash
git --version
```

Vous devriez voir :

```bash
git version 2.34.1
```

## 02. Création d'un Environnement Virtuel



1. Pour créer un environnement virtuel, placez-vous dans le répertoire où vous souhaitez le créer:

```bash
cd /home/romy/Dev
```

2. Créer votre environnement virtuel en lui donnant un nom (ici `my-first-app`):

```bash
python -m venv my-first-app
```

3. Entrez dans votre envrionnement virtuel:

```bash
source my-first-app/bin/activate
```

4. Le prompt vous indique que vous êtes bien dans l'environnement virtuel `my-first-app` :

```bash
(my-first-app) romy@HAL9000:~/Dev$ 
```

Pour sortir de votre environnement virtuel, tapez :

```bash
deactivate
```

Les prompts changent alors :

```bash
(my-first-app) romy@HAL9000:~/Dev$ deactivate
romy@HAL9000:~/Dev$
```

