# <p align="center">Microblogging : Musicat </p>

Objectif du projet : créer un réseau social pour partager des photos au sein d'une communauté fan de chats et musiques 

## Organisation de travail
- Agile - Scrum
- Journaux de bord
- MOB programming et pair programming

## Fonctionnalités 
- Création de compte pour un user
- Page de connexion et déconnexion 
- Page de profil
- Créer des posts

## 🛠️ Tech Stack
- Docker
- PHP  (version 8.x)
- Laravel (version 10.x)
- PostgreSQL
- PHPUnit

![image](https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white 
) ![image](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white) ![image](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white) ![image](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white) ![image](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)

## Mes missions pendant ce projet   
- Connecter la base de données
- Ajouter les fonctionnalités pour personnaliser les profils
- Ecrire les tests unitaires 
  
## Configuration

#### [Windows] Pré-requis : installer WSL 2

🟡 Si vous ne l'avez toujours pas fait, installez WSL 2. Voir la [doc officielle de WSL 2](https://learn.microsoft.com/fr-fr/windows/wsl/install).

En résumé, WSL (= Windows Sub-system for Linux) installe un système d'exploitation Linux par dessus votre système d'exploitation Windows, mais sans la partie graphique.

Ce (sous-)système Linux, est un vrai OS, il vient avec un Terminal de commande et son propre système de fichiers, **indépendant de votre système de fichiers Windows**.

🚩 Pour un environnement de développement optimal, nous vous recommandons fortement d'utiliser ce système Linux **pour tous vos projets**, ainsi que pour tous les outils ou librairies associées que vous seriez amené à installer. Utilisez donc toujours votre shell WSL, et créez vos fichiers et projets toujours sur le système de fichiers WSL.

Pourquoi ?
- Les outils de shell Linux sont aujourd'hui un standard dans le développement.
- Intéragir depuis le shell WSL avec des fichiers existants sur votre système de fichiers Windows peut vous exposer à des problèmes de (fortes) lenteurs. Avec Docker, cela peut même devenir quasi inutilisable. Faites-vous du bien, utilisez WSL par défaut 🫶

Sur le site officiel de WSL, vous trouverez plus d'infos sur le [Stockage de fichiers et performances dans les systèmes de fichiers](https://learn.microsoft.com/fr-fr/windows/wsl/filesystems#file-storage-and-performance-across-file-systems).

## Première installation sur votre machine

###  [Windows / Mac / Linux] Pré-requis : installer Docker 

🟡 Installer Docker via le [site officiel de Docker](https://docs.docker.com/get-docker/).

Pour les Windows, choisir l'option d'installation de Docker **avec WSL 2**.

---

🟡 S'assurer ensuite qu'il tourne en local sur votre machine :

```
docker info
```


### [Windows] Pré-requis : cloner le projet 🚩sur le système de fichiers Linux (WSL)🚩

🟡 Si vous avez cloné ce template projet microblogging directement sur le filesystem WSL, bravo vous avez bien suivi le premier pré-requis, vous pouvez passer à l'étape suivante 🎉

Si ce template projet se trouve sur votre système de fichiers Windows, clonez-le de nouveau, mais cette fois-ci sur le système de fichiers WSL.

---

🚩 Comment cloner le projet sur le système de fichiers WSL ?

- Ouvrez le terminal WSL
- Rendez-vous dans votre répertoire `HOME` de votre système de fichiers WSL
    ```
    cd ~
    ```
- Assurez-vous que votre répertoire courant ne commence pas par `/mnt/c/`.

- S'il commence par `/mnt/c/`, ce n'est pas bon, car cela signifie que vous êtes toujours sur systeme de fichiers Windows, comme mentionné dans la documentation sur les [systèmes de fichiers de WSL](https://learn.microsoft.com/fr-fr/windows/wsl/filesystems#file-storage-and-performance-across-file-systems).

- Si vous êtes bien sur le système de fichiers WSL, c'est bon, créez ou allez dans votre répertoire projet, puis clonez le projet de manière classique.
  

###  [Windows / Mac / Linux] Pré-requis : configurer l'environnement de développement du projet

Ce projet a été pré-configuré pour vous permettre une installation rapide et automatique de toutes ses dépendances (outils de ligne de commandes PHP, Laravel et ses librairies, des extensions VSCode adaptées au développement PHP). Pour cela on va utiliser la fonctionnalité de ["Dev Containers" de VSCode](https://code.visualstudio.com/docs/devcontainers/containers).

---

🟡 Ouvrir le projet dans VSCode. Les fichiers et dossiers du repo doivent constituer **la racine** de l'arborescence du projet sous VS Code.

❗️ Ouvrez bien le projet directement depuis le dossier racine, via "Open Folder", ou via `code .`. L'extension Dev Container ne fonctionne pas depuis un "workspace", donc n'ouvrez pas le dossier via "Add Folder to Workspace".

---

🟡 Copier le fichier `.env.example` vers `.env`

```
cp .env.example .env
```

❗️ Cette étape est **essentielle** pour permettre la bonne configuration de l'environnement Docker du projet.

---

🟡 Installer l'extension VSCode "Dev Containers"

---

🟡 Ré-ouvrir le projet dans VSCode **dans Docker** avec la commande "Reopen in Container"

Le projet s'ouvre normalement dans une nouvelle fenêtre VSCode, et démarre le téléchargement des images Docker, puis la construction et l'exécution des containers associés. Cela peut prendre quelques minutes en fonction de la bande passante réseau et de la puissance de votre machine.

À cette étape, VSCode vous propose normalement d'ouvrir les logs Docker, faites-le, essayez de comprendre ce qui s'y déroule, et assurez-vous qu'il n'y ait pas d'erreur.

❓ Une fois terminé, votre projet tourne "sous Docker". Selon vous, qu'est ce que cela signifie ?

❓ Observez également les extensions VSCode installées. D'où viennent ces extensions PHP / Laravel ?


### Démarrer l'application Laravel

🟡 Ouvrir le terminal de VSCode.

❓ Observez-bien le prompt de votre terminal VSCode. Selon vous, où s'exécute ce terminal ?

---

🟡 Installer les dépendances PHP via `composer`

```
composer install
```

Composer est le package manager par défaut de PHP (l'équivalent de `npm` en Node/JS). Les dépendances du projet (i.e. les librairies externes nécessaires) sont décrites dans le fichier `composer.json`. Une fois téléchargées elles sont installées dans le dossier `vendor`.

❓ Selon vous, doit-on commiter ce dossier `vendor` dans le git du projet ?

---

🟡 Générer votre "application encryption key" nécessaire à toute application Laravel

```
php artisan key:generate
```

Cette commande génère une clé qui est ensuite stockée dans la variable `APP_KEY` de votre `.env`.

---

🟡 Lancer le serveur web interne à Laravel

```
php artisan serve
```

Vous devriez voir la page par défaut de Laravel en ouvrant l'url indiquée (http://127.0.0.1:8000 si tout se passe bien).

🎉 Bravo, vous l'avez fait, vous avez une application Laravel qui tourne sous Docker !

À ce stade, prenez le temps de vous familiariser avec le fonctionnement de Laravel, en parcourant la doc officielle (fortement recommandé) ou en suivant quelques tutos. Voir les liens à la fin de ce README.


### Gestion de la base de données (PostgreSQL)

🟡 Accéder à l'interface d'admin "pgAdmin" via http://localhost:5050/

---

🟡 Une fois connecté à "pgAdmin", configurer la connexion à votre base de données locale, en ajoutant un nouveau "server".

Les identifiants de connexion sont les mêmes que ceux configurés dans le `docker-compose.yml` (et le `.env`).

❗️ Un détail important lié à Docker : le "host" de connexion correspond à l'url du PostgreSQL **à l'intérieur** du réseau Docker. Plutôt que de chercher l'adresse IP interne de votre PG (ce qui est tout à fait possible si vous avez envie d'un défi supplémentaire), vous pouvez utiliser directement le nom défini au sein du `docker-compose.yml` pour le service PG (= `pgsql`).

🎉 Une fois connecté, vous devriez voir une base nommée `microblogging` (i.e le nom correspondant à la variable `DB_DATABASE` du `.env`). Notez que la base existe mais est vide.

---

🟡 Initialiser la base de données, en effectuant les migrations Laravel existantes par défaut.

```
php artisan migrate
```

À ce stade, observez les tables créées dans votre base PG, et comprenez le lien avec les fichiers présents dans le dossier `database/migrations` du projet.

## Lancer docker et les serveurs 

###  Lancement docker

* Ouvrir Docker 
* Dans terminal, vérifier que Docker est bien lancé en tapant : docker info
* Lancer le container en appuyant sur le bouton play 

###  Lancement serveur

* Ouvrir le projet dans VS code
* Pour lancer le server back faire la cmd ```php artisan serve```
*  lancement du serveur ‘front’ en local avec la commande ```npm run dev```


## À propos de Laravel

<p><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="200" alt="Laravel Logo"></a></p>

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

-   [Simple, fast routing engine](https://laravel.com/docs/routing).
-   [Powerful dependency injection container](https://laravel.com/docs/container).
-   Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
-   Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
-   Database agnostic [schema migrations](https://laravel.com/docs/migrations).
-   [Robust background job processing](https://laravel.com/docs/queues).
-   [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

### Se familiariser avec Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

You may also try the [Laravel Bootcamp](https://bootcamp.laravel.com), where you will be guided through building a modern Laravel application from scratch.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 2000 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## 🙇 Auteurices 

Alexis Chentre, Quentin Kerzelec, Myriam Le Nahelec, Eline Longépée
        
## Visuels du réseau social
![Alt text](/z_screenshots/1-login.png "accueil")
![Alt text](/z_screenshots/2-allposts.png "all posts")
![Alt text](/z_screenshots/3-addposts.png "ajout post")
![Alt text](/z_screenshots/4-userprofile.png "user profile")


