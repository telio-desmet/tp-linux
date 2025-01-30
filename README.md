# README
___
Télio Desmet
___
# TP Linux
## Références
  
- Documents issus de vos propres recherches sur Internet

- Si vous le souhaitez, le [document compagnon du MOOC « Maîtriser le shell Bash »](http://www.opimedia.be/DS/languages/Bash/MOOC-Maitriser-le-shell-Bash--Document-compagnon--v2-6-2019.pdf), en français et relativement bien fait

## Méthodologie

- Vous utiliserez un éditeur de texte simple pour vos réponses (pas de Google Docs ou autre format riche)

- Vous utiliserez la [syntaxe Markdown](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#quoting-code) (fichiers `.md`) pour rédiger ; Markdown est un langage de balisage léger, facile à lire et à écrire, qui peut être converti en HTML ou en d'autres formats, nativement supporté par GitHub, et très approprié pour écrire de la documentation technique

- Pour chaque question, vous préciserez :

  - la commande utilisée (si une commande est demandée)

  - la sortie de la commande le cas échéant (ce qui s'affiche à l'écran)

  - votre réponse argumentée si nécessaire

- La commande doit être clairement différenciée de la sortie en étant précédée d'un caractère de prompt (`$`). Par exemple :

  

```bash

$ echo "ceci est la sortie de la commande"

ceci est la sortie de la commande

```

  

- Vous utiliserez la syntaxe Markdown de code (\`\`\`) pour formater les commandes et les sorties de commandes

- Vous versionerez ces fichiers-réponses avec Git

  

## Travaux pratiques

  

### 1. Gestion de fichiers

  

- Commandes : `pwd, cd, ls, file, less, head, tail, mkdir, cp, mv, rm, rmdir, touch, echo, set, unset, export, env, alias, history, nl, find, grep, sed`

- Notions :

  - « Globbing » de fichier

  - Variables Shell

  - Variables d'environnement (commandes `export` et `env`)

  - Alias de commandes (commande `alias`)

  - Historique de commandes

  - Redirection d'entrées/sorties (STDOUT, STDERR, STDIN, utilisations des caractères `<` et `>` dans les commandes)

  - « Piping » (caractère `|` dans les commandes, bien comprendre différence avec `>`)

  - Sous-commandes (`$(commande a executer)` à l'intérieur d'une autre commande)

  - Expressions régulières

  - Bien comprendre `find` (recherche fichiers) et `grep` (recherche dans fichiers)

  - Commande `sed` pour éditer un fichier en ligne de commande (automatiquement), par exemple pour remplacer une chaîne de caractère par une autre

  - Commandes d'archivage et de compression : `tar`, `gzip`, `gunzip` `bz2`, `xz`

  

1. Ouvrir un terminal

2. Afficher le répertoire courant

```

$ pwd

Sortie : /mnt/c/Users/telio

```

3. En utilisant un chemin absolu, aller sur le répertoire `/etc`

```

$ cd ./etc

```

4. En utilisant un chemin relatif, aller sur le répertoire `/etc/skel`

```

$ cd skel

```

5. En utilisant un chemin relatif, remonter sur `etc`

```

$ cd ..

```

6. Afficher les fichiers du répertoire courant

```

$ ls

Sortie : la liste des fichiers

```

7. Même chose en « affichage détaillé »

```

$ ls -l

Sortie :

total 788

drwxr-xr-x 2 root root       4096 Sep 27 22:14 PackageKit

drwxr-xr-x 7 root root       4096 Sep 27 22:14 X11

-rw-r--r-- 1 root root       3444 Jul  5  2023 adduser.conf

...

```

8. Afficher tous les fichiers du répertoire courant qui commencent par `s`

```

$ ls s*

```

9. Lancer la commande qui permet de déterminer le type de contenu dans le fichier `/etc/group`

```

$ file /etc/group

Sortie : /etc/group: ASCII text

```

10. Afficher les cinq dernières lignes du fichier `/etc/group`

```

$ tail -5 group

Sortie :

landscape:x:105:

polkitd:x:990:

admin:x:106:

netdev:x:107:test

test:x:1000:

```

11. Exécuter la commande qui revient directement à votre répertoire personnel

```

$ cd

```

12. Créer un répertoire nommé `temp` dans votre répertoire personnel

```

$ mkdir temp

```

13. Copier le fichier `/etc/passwd` dans le répertoire `temp`

```

$ cp /etc/passwd ./

```

14. Copier le répertoire `/etc/ppp` dans le répertoire courant (ignorer toutes les erreurs "permission denied") (utiliser un autre répertoire pas trop « gros », comme `/etc/ssh`, si `/etc/ppp` n'est pas sur votre système)

```

$ sudo cp -r /etc/ssh .

```

15. Renommer le répertoire `ppp` du répertoire courant en `peers`

```

$ mv ssh peers

```

16. Mettre à jour le timestamp du fichier `temp/passwd` à la date et heure courantes

```

$ touch passwd

```

17. Créer un nouveau fichier vide nommé `test` dans le répertoire `temp`

```

$ touch test

```

18. Supprimer le fichier `temp/passwd`

```

$ rm passwd

```

19. Supprimer le répertoire `peers`

```

$ sudo rm -r peers

```

  

### 2. Fonctionnalités du Shell

  

1. Afficher le contenu de la variable `HOME`

```

$ echo $HOME

```

Sortie : /home/test

2. Afficher toutes les variables shell avec leur contenu

```

$ env

Sortie :

SHELL=/bin/bash

WSL2_GUI_APPS_ENABLED=1

WSL_DISTRO_NAME=Ubuntu

NAME=La-plus-belle

PWD=/home/test/temp

LOGNAME=test

MOTD_SHOWN=update-motd

HOME=/home/test

LANG=C.UTF-8

WSL_INTEROP=/run/WSL/421_interop

...

```

3. Afficher le contenu de la variable `TEST` (noter que cette variable n'a en fait aucun contenu actuellement)

```

$ echo $TEST

```

4. Changer le shell courant afin qu'un message d'erreur s'affiche quand une variable indéfinie est utilisée

```

$ set -u

```

5. Modifier la variable `PATH` pour ajouter le répertoire `/opt`

```

$ export PATH=$PATH:/opt

```

6. Créer une variable d'environnement appelée `EVENT` et lui donner la valeur "maintenant" en utilisant une seule commande

```

$ export EVENT="maintenant"

```

7. Afficher toutes les variables d'environnement

```

$ env

Sortie :

SHELL=/bin/bash

WSL2_GUI_APPS_ENABLED=1

WSL_DISTRO_NAME=Ubuntu

EVENT=maintenant

NAME=La-plus-belle

PWD=/home/test/temp

LOGNAME=test

MOTD_SHOWN=update-motd

HOME=/home/test

LANG=C.UTF-8

WSL_INTEROP=/run/WSL/421_interop

...

```

8. Créer un alias dans le shell courant pour la commande `ls` de telle sorte que ça lance la commande `ls -a`

```

$ alias ls='ls -a'

```

9. Afficher tous les alias du shell courant

```

$ alias

Sortie :

alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

alias egrep='egrep --color=auto'

alias fgrep='fgrep --color=auto'

alias grep='grep --color=auto'

alias l='ls -CF'

alias la='ls -A'

alias ll='ls -alF'

alias ls='ls -a'

```

10. Supprimer l'alias défini en 8 du shell courant

```

$ unalias ls

```

11. Afficher une liste des commandes précédemment exécutées

```

$ history

Sortie :

   1  echo 'export PATH=$PATH:/mnt/c/Program\ Files/Multipass' >> ~/bashrc

    2  echo 'export PATH=$PATH:/mnt/c/Program\ Files/Multipass' >> ~/.bashrc

    3  source ~/.bashrc

    4  multipass version

    5  sudo snap install multipass

    6  multipass version

    7  multipass list

    8  multipass find

    9  multipass shell

   10  exit

   11  pwd

   12  ls

   13  cd ..

   14  ls

   15  cd ./etc

   16  cd /skel

   17  ls

   18  cd skel

   19  cd .

   20  cd ..

   ...

```

12. Re-exécuter la dernière commande `ls` de l'historique

```

$ !ls

Sortie :

ls

temp  test

```

13. Changer le nombre maximum de commandes stockées dans l'historique du shell courant (2000)

```

$ export HISTSIZE=2000

```

14. Exécuter la commande `ps -ef` et utiliser un *pipe* pour passer la sortie à la commande `less`

15. Afficher tous les fichiers dans la structure du répertoire `etc` (sous-répertoires inclus) dont le groupe propriétaire est le groupe `lp` (ou n'importe quel autre groupe existant si le groupe `lp` n'existe pas sur votre système)

```

$ find /etc -group lp

Sortie :

find: ‘/etc/polkit-1/rules.d’: Permission denied

find: ‘/etc/ssl/private’: Permission denied

find: ‘/etc/credstore’: Permission denied

find: ‘/etc/credstore.encrypted’: Permission denied

```

16. Afficher tous les lignes dans le fichier `etc/passwd` qui contiennent au moins trois nombres d'affilé

```

$ grep -E '[0-9]{3,}' /etc/passwd

Sortie :

sync:x:4:65534:sync:/bin:/bin/sync

_apt:x:42:65534::/nonexistent:/usr/sbin/nologin

nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin

systemd-network:x:998:998:systemd Network Management:/:/usr/sbin/nologin

systemd-timesync:x:996:996:systemd Time Synchronization:/:/usr/sbin/nologin

dhcpcd:x:100:65534:DHCP Client Daemon,,,:/usr/lib/dhcpcd:/bin/false

messagebus:x:101:101::/nonexistent:/usr/sbin/nologin

syslog:x:102:102::/nonexistent:/usr/sbin/nologin

systemd-resolve:x:991:991:systemd Resolver:/:/usr/sbin/nologin

uuidd:x:103:103::/run/uuidd:/usr/sbin/nologin

landscape:x:104:105::/var/lib/landscape:/usr/sbin/nologin

polkitd:x:990:990:User for polkitd:/:/usr/sbin/nologin

test:x:1000:1000:,,,:/home/test:/bin/bash

```

17. Afficher le fichier `etc/passwd` avec toutes les occurrences de `root` remplacées par `XXXX`

```

$ sed 's/root/XXXX/g' /etc/passwd

Sortie :

XXXX:x:0:0:XXXX:/XXXX:/bin/bash

daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin

bin:x:2:2:bin:/bin:/usr/sbin/nologin

sys:x:3:3:sys:/dev:/usr/sbin/nologin

sync:x:4:65534:sync:/bin:/bin/sync

games:x:5:60:games:/usr/games:/usr/sbin/nologin

man:x:6:12:man:/var/cache/man:/usr/sbin/nologin

lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin

mail:x:8:8:mail:/var/mail:/usr/sbin/nologin

news:x:9:9:news:/var/spool/news:/usr/sbin/nologin

uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin

proxy:x:13:13:proxy:/bin:/usr/sbin/nologin

www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin

backup:x:34:34:backup:/var/backups:/usr/sbin/nologin

...

```

  

### 3. Compression

  

1. En utilisant l'option « verbose », créer un fichier tar appelé `etcppp.tar` qui contient le contenu du répertoire `etc/ppp` (ignorer les messages d'erreurs potentiels)

```

$ tar -cvf etcppp.tar --ignore-failed-read /etc/ssh

```

2. Afficher le contenu de l'archive `etcppp.tar` (sans l'extraire)

```

$ tar -tf etcppp.tar

Sortie :

etc/ssh/

etc/ssh/ssh_config.d/

etc/ssh/ssh_config

```

3. Créer un répertoire `extraction-tar` dans le répertoire courant

```

$ mkdir extraction-tar

```

4. Extraire le contenu de l'archive `etcppp.tar` dans le répertoire `extraction-tar`

```

$ tar -xvf etcppp.tar -C extraction-tar

```

5. Compresser l'archive `etcppp.tar` en utilisant la commande `gzip`, sans écraser le fichier `etcppp.tar` ; le fichier résultant devra se nommer `etcppp.tar.gz`

```

$ gzip -c etcppp.tar > etcppp.tar.gz

```

6. Compresser l'archive `etcppp.tar` en utilisant la commande `bzip2`, sans écraser ; le fichier résultant devra se nommer `etcppp.tar.bz2`

```

$ sudo apt install bzip2

$ bzip2 -c etcppp.tar > etcppp.tar.bz2

```

7. Comparer les tailles des deux fichiers compressés (`.gzip` et `.bz2`) ; lequel des deux algorithmes semble avoir un meilleur taux de compression ?

```

$ ls -lh etcppp.tar.gz > etcppp.tar.bz2

Sortie :

-rw-r--r-- 1 test test 1.1K Jan 18 18:55 etcppp.tar.bz2

-rw-r--r-- 1 test test  980 Jan 18 18:51 etcppp.tar.gz

On remarque ici que etcppp.tar.gz est plus léger que l'autre donc gzip semble avoir un meilleur taux de compression

```

8. Supprimer le fichier `etcppp.tar`

```

$ rm etcppp.tar

```

9. Décompresser le fichier `etcppp.tar.gz`

```

$ gunzip etcppp.tar.gz

  

```

  

### 4. Obtenir de l'aide

  

- `man` et ses options (pour les commandes générales et les fichiers de configuration), `help` (pour les commandes shell seulement, comme `cd`), `whatis`, `info`

- Sur n'importe quelle commande, souvent une option `--help` (parfois `-h`) pour une aide plus brève

  

### 5. Identifier et résoudre les problèmes liés à une commande

  

Étapes générales de résolution d'un problème (valable au-delà des problèmes de commandes systèmes) :

  

- **Réunir des informations** : lire les messages d'erreurs, essayer une autre commande basique sur le même fichier (problème d'existence/d'accès ?)

- **Déterminer la cause probable** : utiliser `--help` ou `man/info`, internet (notamment, faire une recherche sur le message d'erreur spécifique), un ami/collègue, voire l'admin système (en fournissant les détails)...

- **S'assurer que toutes les actions sont documentées** : en a-t-on compris suffisamment et a-t-on tout ce qu'il faut pour aller à la fin de la procédure ? Pourra-ton « défaire » chaque étape si ça ne fonctionne pas ?

- **Effectuer les actions** : s'assurer que chaque action produit le résultat intermédiaire attendu avant de poursuivre ; toute la procédure tombe par terre sinon, et il pourra être difficile de « défaire » si on ne sait pas ce qui a été « fait »

- **Vérifier que le problème est résolu** : si ce n'est pas le cas, faut-il « défaire » ce qui a été essayé auparavant ? Souvent oui, car ces actions pourraient interférer avec une nouvelle solution potentielle et/ou créer des problèmes futurs

- **Vérifier, dans la mesure du possible, qu'il n'y a pas d'autres problèmes** : parfois un *fix* d'un problème cause d'autres problèmes d'une ampleur encore plus importante (problème d'accès d'un utilisateur ? => on édite en root un fichier de configuration pour accorder les droits => on ferme par la même les droits d'autres utilisateurs, ou bien on introduit un problème de sécurité...)

- **Prendre note de la solution** : trouvez un système qui vous permet de documenter les solutions qui ont fonctionné pour un problème donné. Se dire « c'est bon, je m'en souviendrai » *ne fonctionne quasiment jamais* pour un problème au-delà du trivial. Utilisez plutôt un outil numérique qui permettra des recherches aisées, des copier/coller de lignes de commandes, un système de tags, etc.

  

1. Essayer d'exécuter la commande `ls /var/logs`

```

$ ls /var/logs

Sortie:

ls: cannot access '/var/logs': No such file or directory

```

2. La commande précédente échoue. Lire le message d'erreur et expliquer pourquoi

```

La commande échoue car le dossier var/logs n'existe pas.

```

3. Quelle commande pourrait-on exécuter pour déterminer le nom correct du répertoire de logs ?

```

$ ls /var

Sortie :

backups  cache  crash  lib  local  lock  log  mail  opt  run  snap  spool  tmp

```

4. Exécuter la commande correcte

```

$ ls /var/log

Sortie :

README            bootstrap.log  dmesg.0     faillog         landscape  unattended-upgrades

alternatives.log  btmp           dmesg.1.gz  fontconfig.log  lastlog    wtmp

apt               dist-upgrade   dmesg.2.gz  journal         private

auth.log          dmesg          dpkg.log    kern.log        syslog

```

5. Essayer `head -N 7 /etc/passwd`

```

$ head -N 7 /etc/passwd

Sortie:

head: invalid option -- 'N'

```

6. Marche pas. Quelle commande peut-on exécuter pour connaître la bonne option ?

```

On peut effectuer :

$ head --help

```

7. Exécuter la commande correcte

```

$ head -n 7 /etc/passwd

```

8. Essayer `cp /etc/passwd /var`

```

$ cp /etc/passwd /var

```

9. Boum. Que se passe-t-il ?

On a pas les permissions.

10. Comment ferait-on pour effectivement travailler sur une copie du fichier ?

```

$ sudo cp /etc/passwd /var

```

  

### 6. Configurer les comptes groupes

  

(L'importance des comptes utilisateurs et groupes en termes de sécurité ne peut pas être suffisamment soulignée)

  

- Notions : ajouter/modifier/supprimer des groupes ; ajouter/supprimer un utilisateur à un groupe ; groupe primaire / groupes secondaires d'un utilisateur

- Typiquement, on va créer un groupe pour chaque service, un groupe pour un projet sur lequel travaillent plusieurs personnes (potentiellement pas du même service), un groupe pour les différents titres (ingénieurs, managers, etc.) ; cela permettra une gestion individuelle des permissions sur chaque groupe

- Commandes : `id, groups, chgrp, newgrp, grpadd, groupmod, groupdel, usermod, gpasswd`

- Fichiers : `/etc/group`, `/etc/gshadow`

  

1. Afficher l'ID de l'utilisateur courant et ses groupes

```

$ id

Sortie :

uid=1000(test) gid=1000(test) groups=1000(test),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),107(netdev)

```

2. Afficher les groupes du compte root. Quel est son groupe primaire ? Quels sont ses groupes secondaires ?

```

$ id root

Sortie :

uid=0(root) gid=0(root) groups=0(root)

Son groupe primaire est 0(root)

Ses groupes secondaires sont 0(root)

```

3. Rechercher la ligne concernant le groupe `adm` dans `etc/group` ; explicitez les informations données sur cette ligne

```

$ grep '^adm:' /etc/group

Sortie :

adm:x:4:syslog,test

Il y a le nom du groupe, le mdp, l'id du groupe et les autres membres

```

4. Déterminer le propriétaire et le groupe propriétaire du fichier `/etc/group`

```

$ ls -l /etc/group

Sortie :

-rw-r--r-- 1 root root 771 Jan 15 16:11 /etc/group

Le propriétaire est root et le groupe propriétaire est root

```

5. Afficher les informations du compte groupe `games` (ou un autre groupe quelconque si votre système ne définit pas le groupe `games`)

```

$ grep '^games:' /etc/group

Sortie :

games:x:60:

```

6. Afficher, pour le compte groupe `games`, la ligne d'informations issue du fichier `/etc/passwd`

```

$ grep '^games:' /etc/passwd

Sortie :

games:x:5:60:games:/usr/games:/usr/sbin/nologin

```

7. Exécuter `su -` (différence avec `su` ?)

```

$ su -

Sortie :

Password:

su: Authentication failure

  

La différence entre les 2 est que su change l'utilisateur mais su - change l'utilisateur ET l'environnement

```

8. Créer un nouveau groupe `test`

```

$ sudo groupadd testexo

```

9. Afficher les informations du compte groupe `test`

```

$ grep '^testexo:' /etc/group

Sortie :

testexo:x:1001:

```

10. Changer le nom en `grouptest`

```

$ sudo groupmod -n grouptest test

```

11. Ajouter votre compte utilisateur personnel en tant que second membre du groupe `grouptest` *sans écraser vos autres groupes actuels* (trouvez l'option avant d'exécuter la commande)

```

$ sudo usermod -a -G grouptest test

```

12. Expliquez ce que fait la commande `find / -group grouptest -exec chgrp compta {} \;`

```

La commande recherche tout les fichiers appartenant au groupe grouptest et essaie de changer le propriétaire

```

13. Supprimer le groupe `grouptest`

```

$ sudo groupdel grouptest

```

14. Répondez à la question suivante de l'un de vos utilisateurs : « Je veux créer des fichiers qui auront pour groupe propriétaire le groupe `projet-x`. Comment je fais pour changer temporairement mon groupe primaire pour que les fichiers soient créés avec le bon groupe ? »

```

$ newgrp projet-x

$ sudo gpasswd projet-x

  

```

  

### 7. Configurer un administrateur de groupe

  

Créez un utilisateur `dummy`. Créez un nouveau groupe `supports` et ajoutez-y l'utilisateur `dummy`. Faites de `dummy` un administrateur du groupe. Confirmez ce nouveau statut en examinant `/etc/gshadow`. Pour tester, loggez-vous en tant que `dummy` et ajoutez l'utilisateur `bin` au groupe `supports` (vous devriez alors pouvoir le faire sans `sudo`) puis affichez les groupes de `bin`.

  

```

$ sudo useradd dummy

$ sudo groupadd supports

$ sudo usermod -aG supports dummy

$ sudo nano /etc/gshadow

On modifie la ligne "supports:::dummy "

$ sudo cat /etc/gshadow | grep supports

$ sudo passwd dummy

$ su - dummy

.

.

.

.

```

  

### 8. Configurer les comptes utilisateurs

  

- Notions : ajouter/modifier/supprimer des utilisateurs, permissions utilisateurs

- Commandes : `useradd, passwd`

- Fichiers : `/etc/passwd, /etc/shadow, /etc/group, /etc/gshadow`

  

1. Afficher les informations du compte `bin` (y compris le shell et le répertoire utilisateur)
   
````

````
2. Afficher les informations de mot de passe de votre compte (y compris le mot de passe haché)

3. Créer un utilisateur `nadine` en spécifiant explicitement la création du répertoire utilisateur (sinon ce répertoire n'est pas forcément créé)

4. Appliquer un mot de passe fort pour `nadine` : `couscousavecdesmerguezdanstaface`

5. Afficher les valeurs par défaut utilisées lorsqu'un nouveau compte est créé

6. Afficher le fichier qui contient les informations de temps d'expiration par défaut pour les mots de passe

7. Afficher le fichier qui contient les informations sur le shell par défaut

8. Supprimer le compte `nadine` ainsi que son répertoire utilisateur (en une seule commande) 