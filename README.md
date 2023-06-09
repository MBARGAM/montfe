## ETAPES D'INSTALLATION DE L'INTERFACE ADMINISTRATEUR JIDISSET

* Introduction

Ce document fournit des instructions étape par étape sur la façon de cloner l'INTERFACE à partir de GitHub.

## Tuto pour l'installation de symfony et nodejs

# Sur Mac os et windows

- la version de symfony utilisée est la 5.4  et la version de nodejs est la 14.17.6

## Prérequis pour que cela fonctionne en fonction de votre OS
#  ----------------------------------
# 	Soft		Version
#	-----------------------
# 	nodejs  	v16.19.1

#   Apache		2.4.48 (MAC OS X)
#	PHP 		8.0.8 s(MAC OS X)
#	MariaDB		10.5.18
#  MySQL        5.7.34

Avant de commencer, assurez-vous que vous avez les éléments suivants:

- Git installé sur votre ordinateur

- Composer installé sur votre ordinateur

- Node.js installé sur votre ordinateur

- serveur Apache et mysql installé sur votre ordinateur

* Clonage du projet :

pour cloner le projet , procedez comme suit :

1) # Ouvrez la ligne de commande sur votre ordinateur et copier/coller la commande suivante afin de telecharger le projet :

- git clone https://github.com/MBARGAM/jidisset_interface.git

  Une fois la commande exécutée, vous devriez voir le projet cloné dans votre répertoire.

2) # Ouvrir votre IDE  et charger le projet cloné ou acceder au projet cloné avec votre ligne de commande

3) # executez les  commandes suivantes pour installer les dépendances du projet avec Composer:

    - composer  install

           --pour installer webpack encore
    - composer require symfony/webpack-encore-bundle
   
           -- Installation du multi-langue  avec translation
    - composer require symfony/translation

           --installation du mailer
    - composer require symfony/mailer

          -- installation de  snappy pour la generation des pdf
          -- telecharger la version correspondant a votre OS et l'installer sur votre machine
    - installer wkhtmltopdf sur votre machine lien de telechargement : https://wkhtmltopdf.org/downloads.html

          --saisir la commande dans le terminal 
    - composer require knplabs/knp-snappy-bundle

          -- installation pour l'authentification via google
          -- executer les commandes dans le terminal : 
    - composer require knpuniversity/oauth2-client-bundle
   
    - composer require league/oauth2-google
   
             -- saisir vos identifiants google dans le fichier .env.local
             -- ce sont les identifiants de l'application google que vous avez créée sur google cloud platform 
    - OAUTH_GOOGLE_CLIENT_ID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    - OAUTH_GOOGLE_CLIENT_SECRET=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
            
             -- installation de la librairie deepl pour la traduction des textes venant de l'api deepl 
             Nb: deepl est une api de traduction qui permet de traduire des textes en plusieurs langues
             -- creer un compte sur deepl et recuperer votre auth_key et la placer chaque fois que vous voulez utiliser l'api deepl
    - composer require symfony/http-client 
   
           --pour activer sass dans webpack encore
    - npm install sass-loader sass webpack --save-dev

    - npm run watch

          -- Installation de Jquery
    - npm install jquery

          --installation de leaflet pour la carte
    - npm install leaflet
    - npm run dev


4) # Tapez la commande suivante pour démarrer le serveur de développement de Symfony:

    - symfony server:start

5) # Modifiez les paramètres de configuration dans le fichier .env en fonction de la base de données que vous souhaitez utiliser

   sur le ligne :  DATABASE_URL="mysql://root:root@127.0.0.1:8889/jidissetInterface?serverVersion=8&charset=utf8mb4"

   ## NB: faire attention au port de votre base de données en mettant le bon port  et au nom de votre base de données

    - soit vous mettez la ligne en commentaire si vous utilisez une autre base de donnee autre que mysql

    - soit vous modifiez les parametres suivant afin de definir le nom de votre base de données  :

            DATABASE_URL="mysql://votreIdentifiant:votreMotDePasse@adresseEnLocal/nomDeVotreBase?serverVersion=8&charset=utf8mb4"

6) # Créer une base de donnee grace a la commande :

    - php bin/console doctrine:database:create

7) # Faire migrer les migtrations  avec la commande :

   - php bin/console doctrine:migration:migrate

8) # Importer le fichier fichier.sql se trouvant dans   /public/sql/  dans la base de données que vous avez créée afin de remplir la base de données avec des données de test
    
    - un administrateur par défaut avec les identifiants suivants:

   ##  ID: JUSTYNADMIN
   ##  MDP: admin
   
   - un professeur par défaut avec les identifiants suivants:
   ##  ID: JUSTYNPROF
   ##  MDP: admin

    - un eleve par défaut avec les identifiants suivants:
    ##  ID: JUSTYNELEVE
    ##  MDP: admin

9) ##  pour le mailing :
         -  modifier le fichier .env  (ligne 43) en mettant MAILER_DSN du service que vous utilisez pour envoyer les mails
        
         ## exemple pour MAILTRAP:

          MAILER_DSN=smtp://eac504557751ea:e3fedd4821b939@smtp.mailtrap.io:2525?encryption=tls&auth_mode=login

10) ## pour tester le projet en local sur votre machine :

        -- ouvrir votre navigateur et saisir l'url suivante mais si vous etes en ligne , il faut saisir l'url de votre site en ligne dans google cloud platform
    https://127.0.0.1:port   (port par defaut 8000)


Identifiant :
ADMIN :  
 ID: JUSTYNADMIN
    MDP: admin
       email: admin@admin.be
ELEVE : 
 ID: JUSTYNELEVE
    MDP: admin
    email: mbargamarie93@gmail.com
PROF :
    ID: JUSTYNPROF
        MDP: admin
        email: jidisset17@gmail.com


test HILGERSM : eleve  -----  prof   : LONGUEVILLEI

