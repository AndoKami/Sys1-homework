## 1. Générer les clés SSH

- Exécutez la commande suivante pour générer une nouvelle paire de clés SSH : 
```sh
    ssh-keygen -t rsa -b 4096 -f private.key
```
Cette commande génère une paire de clés RSA avec une longueur de clé de 4096 bits et enregistre la clé privée sous private.key.

- Il vous sera demandé de fournir une `passphrase`. Vous pouvez choisir d'entrer une phrase d'authentification ou de la laisser vide pour ne pas avoir de phrase d'authentification. Notez que la définition d'une phrase de passe ajoute une couche supplémentaire de sécurité.

- La commande génère deux fichiers : private.key (la clé privée) et private.key.pub (la clé publique).

## 2. Copie de la clé publique sur le serveur distant

- Exécutez la commande suivante pour copier la clé publique sur le serveur distant :
``sh
ssh-copy-id -i private.key.pub username@ip

#pour le script.yaml, le nom d'utilisateur doit être "root"
```
- Remplacez private.key.pub par le chemin réel de votre fichier de clé publique, username par le nom d'utilisateur sur le serveur distant, et ip par l'adresse IP du serveur.

- Vous serez invité à saisir le mot de passe du serveur distant. Saisissez le mot de passe pour vous authentifier et copier la clé publique.

**Note** : Si vous avez défini une phrase de passe pour votre clé privée, vous serez invité à la saisir avant de copier la clé.

- La clé publique sera ajoutée au fichier `~/.ssh/authorized_keys` sur le serveur distant, vous permettant de vous authentifier en utilisant la clé privée.

- `ssh-copy-id -i private.key.pub root@ip` ne fonctionnera pas si vous ne mettez pas `PermitRootLogin` à `yes` (c'est mentionné dans [README.md](./README.md) )

## 3. Connexion au serveur à l'aide de la clé privée
- Exécutez la commande suivante pour vous connecter au serveur en utilisant la ``clef privée`` :

``sh
ssh -i private.key username@ip
```
Remplacez private.key par le chemin réel de votre fichier de clé privée, username par le nom d'utilisateur sur le serveur distant, et ip par l'adresse IP du serveur et c'est tout, vous êtes connecté au serveur.

**Note** : 
- Ce fichier fournit des instructions sur la façon de générer et d'utiliser des `clés SSH` en utilisant `ssh-keygen` et `ssh-copy-id` pour envoyer une `clé publique` ; ainsi que sur la façon de se connecter à un serveur en utilisant la `clé privée`.

- Si vous avez défini une phrase de passe pour votre clé privée, vous serez invité à la saisir.

- N'oubliez pas de garder votre clé privée en sécurité et de ne jamais la partager avec des personnes non autorisées. En outre, il est conseillé de définir des passphrases fortes pour vos clés privées afin d'en renforcer la sécurité.