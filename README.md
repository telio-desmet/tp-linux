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
3. En utilisant un chemin absolu, aller sur le répertoire `/etc`
4. En utilisant un chemin relatif, aller sur le répertoire `/etc/skel`
5. En utilisant un chemin relatif, remonter sur `etc`
6. Afficher les fichiers du répertoire courant
7. Même chose en « affichage détaillé »
8. Afficher tous les fichiers du répertoire courant qui commencent par `s`
9. Lancer la commande qui permet de déterminer le type de contenu dans le fichier `/etc/group`
10. Afficher les cinq dernières lignes du fichier `/etc/group`
11. Exécuter la commande qui revient directement à votre répertoire personnel
12. Créer un répertoire nommé `temp` dans votre répertoire personnel
13. Copier le fichier `/etc/passwd` dans le répertoire `temp`
14. Copier le répertoire `/etc/ppp` dans le répertoire courant (ignorer toutes les erreurs "permission denied") (utiliser un autre répertoire pas trop « gros », comme `/etc/ssh`, si `/etc/ppp` n'est pas sur votre système)
15. Renommer le répertoire `ppp` du répertoire courant en `peers`
16. Mettre à jour le timestamp du fichier `temp/passwd` à la date et heure courantes
17. Créer un nouveau fichier vide nommé `test` dans le répertoire `temp`
18. Supprimer le fichier `temp/passwd`
19. Supprimer le répertoire `peers`

### 2. Fonctionnalités du Shell

1. Afficher le contenu de la variable `HOME`
2. Afficher toutes les variables shell avec leur contenu
3. Afficher le contenu de la variable `TEST` (noter que cette variable n'a en fait aucun contenu actuellement)
4. Changer le shell courant afin qu'un message d'erreur s'affiche quand une variable indéfinie est utilisée
5. Modifier la variable `PATH` pour ajouter le répertoire `/opt`
6. Créer une variable d'environnement appelée `EVENT` et lui donner la valeur "maintenant" en utilisant une seule commande
7. Afficher toutes les variables d'environnement
8. Créer un alias dans le shell courant pour la commande `ls` de telle sorte que ça lance la commande `ls -a`
9. Afficher tous les alias du shell courant
10. Supprimer l'alias défini en 8 du shell courant
11. Afficher une liste des commandes précédemment exécutées
12. Re-exécuter la dernière commande `ls` de l'historique
13. Changer le nombre maximum de commandes stockées dans l'historique du shell courant (2000)
14. Exécuter la commande `ps -ef` et utiliser un *pipe* pour passer la sortie à la commande `less`
15. Afficher tous les fichiers dans la structure du répertoire `etc` (sous-répertoires inclus) dont le groupe propriétaire est le groupe `lp` (ou n'importe quel autre groupe existant si le groupe `lp` n'existe pas sur votre système)
16. Afficher tous les lignes dans le fichier `etc/passwd` qui contiennent au moins trois nombres d'affilé
17. Afficher le fichier `etc/passwd` avec toutes les occurrences de `root` remplacées par `XXXX`

### 3. Compression

1. En utilisant l'option « verbose », créer un fichier tar appelé `etcppp.tar` qui contient le contenu du répertoire `etc/ppp` (ignorer les messages d'erreurs potentiels)
2. Afficher le contenu de l'archive `etcppp.tar` (sans l'extraire)
3. Créer un répertoire `extraction-tar` dans le répertoire courant
4. Extraire le contenu de l'archive `etcppp.tar` dans le répertoire `extraction-tar`
5. Compresser l'archive `etcppp.tar` en utilisant la commande `gzip`, sans écraser le fichier `etcppp.tar` ; le fichier résultant devra se nommer `etcppp.tar.gz`
6. Compresser l'archive `etcppp.tar` en utilisant la commande `bzip2`, sans écraser ; le fichier résultant devra se nommer `etcppp.tar.bz2`
7. Comparer les tailles des deux fichiers compressés (`.gzip` et `.bz2`) ; lequel des deux algorithmes semble avoir un meilleur taux de compression ?
8. Supprimer le fichier `etcppp.tar`
9. Décompresser le fichier `etcppp.tar.gz`

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
2. La commande précédente échoue. Lire le message d'erreur et expliquer pourquoi
3. Quelle commande pourrait-on exécuter pour déterminer le nom correct du répertoire de logs ?
4. Exécuter la commande correcte
5. Essayer `head -N 7 /etc/passwd`
6. Marche pas. Quelle commande peut-on exécuter pour connaître la bonne option ?
7. Exécuter la commande correcte
8. Essayer `cp /etc/passwd /var`
9. Boum. Que se passe-t-il ?
10. Comment ferait-on pour effectivement travailler sur une copie du fichier ?

### 6. Configurer les comptes groupes

(L'importance des comptes utilisateurs et groupes en termes de sécurité ne peut pas être suffisamment soulignée)

- Notions : ajouter/modifier/supprimer des groupes ; ajouter/supprimer un utilisateur à un groupe ; groupe primaire / groupes secondaires d'un utilisateur
- Typiquement, on va créer un groupe pour chaque service, un groupe pour un projet sur lequel travaillent plusieurs personnes (potentiellement pas du même service), un groupe pour les différents titres (ingénieurs, managers, etc.) ; cela permettra une gestion individuelle des permissions sur chaque groupe
- Commandes : `id, groups, chgrp, newgrp, grpadd, groupmod, groupdel, usermod, gpasswd`
- Fichiers : `/etc/group`, `/etc/gshadow`

1. Afficher l'ID de l'utilisateur courant et ses groupes
2. Afficher les groupes du compte root. Quel est son groupe primaire ? Quels sont ses groupes secondaires ?
3. Rechercher la ligne concernant le groupe `adm` dans `etc/group` ; explicitez les informations données sur cette ligne
4. Déterminer le propriétaire et le groupe propriétaire du fichier `/etc/group`
5. Afficher les informations du compte groupe `games` (ou un autre groupe quelconque si votre système ne définit pas le groupe `games`)
6. Afficher, pour le compte groupe `games`, la ligne d'informations issue du fichier `/etc/passwd`
7. Exécuter `su -` (différence avec `su` ?)
8. Créer un nouveau groupe `test`
9. Afficher les informations du compte groupe `test`
10. Changer le nom en `grouptest`
11. Ajouter votre compte utilisateur personnel en tant que second membre du groupe `grouptest` *sans écraser vos autres groupes actuels* (trouvez l'option avant d'exécuter la commande)
12. Expliquez ce que fait la commande `find / -group grouptest -exec chgrp compta {} \;`
13. Supprimer le groupe `grouptest`
14. Répondez à la question suivante de l'un de vos utilisateurs : « Je veux créer des fichiers qui auront pour groupe propriétaire le groupe `projet-x`. Comment je fais pour changer temporairement mon groupe primaire pour que les fichiers soient créés avec le bon groupe ? »

### 7. Configurer un administrateur de groupe

Créez un utilisateur `dummy`. Créez un nouveau groupe `supports` et ajoutez-y l'utilisateur `dummy`. Faites de `dummy` un administrateur du groupe. Confirmez ce nouveau statut en examinant `/etc/gshadow`. Pour tester, loggez-vous en tant que `dummy` et ajoutez l'utilisateur `bin` au groupe `supports` (vous devriez alors pouvoir le faire sans `sudo`) puis affichez les groupes de `bin`.

### 8. Configurer les comptes utilisateurs

- Notions : ajouter/modifier/supprimer des utilisateurs, permissions utilisateurs
- Commandes : `useradd, passwd`
- Fichiers : `/etc/passwd, /etc/shadow, /etc/group, /etc/gshadow`

1. Afficher les informations du compte `bin` (y compris le shell et le répertoire utilisateur)
2. Afficher les informations de mot de passe de votre compte (y compris le mot de passe haché)
3. Créer un utilisateur `nadine` en spécifiant explicitement la création du répertoire utilisateur (sinon ce répertoire n'est pas forcément créé)
4. Appliquer un mot de passe fort pour `nadine` : `couscousavecdesmerguezdanstaface`
5. Afficher les valeurs par défaut utilisées lorsqu'un nouveau compte est créé
6. Afficher le fichier qui contient les informations de temps d'expiration par défaut pour les mots de passe
7. Afficher le fichier qui contient les informations sur le shell par défaut
8. Supprimer le compte `nadine` ainsi que son répertoire utilisateur (en une seule commande)
