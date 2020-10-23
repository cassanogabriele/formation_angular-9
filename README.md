## Apprentissage 

## Créer un projet Laravel 
composer create-project --prefer-dist laravel/laravel udemytraining

## Accéder directement au dossier de l'application créée 
code .

## Lancer le serveur avec l'application 
php artisan serve

## Créer un contrôleur (contrôleur vide)
php artisan make::controller MyController

## Créer un contrôleur avec traitements (GET, POST, PUT/PATCH, DELETE)
php artisan make:controller -r ArticleController

## Fichier de migration 
php artisan make:migration create_post_table

## Créer un modèle 
php artisan make:model Article

## Créer les tables 
php artisan migrate

## Annuler la création des tables
php artisan migrate:rollback

## Nettoyer la config de Laravel
php artisan config clear

## Nettoyer le cache 
php artisan cache:clear

## Annuler la migration 
php artisan migrate:reset

## Créer un seeder
php artisan make:seed ArticleSeeder

## Appeler le database seeder
php artisan db:seed

#####################################################################

## Exécuter directement du code PHP (shell -> exit pour quitter)
php artisan tinker

## Récupérer toutes les catégories 
App\Category::all();

## Récupérer une catégorie aléatoire
App\Category::all()->random(1)->first->id;

#####################################################################

## Middleware 
Un Middleware va fournir un mécanisme pratique pour filtrer les requêtes HTTP qui vont entrer dans l'application.

middleware autth(voir si l'utilisateur est authentifié)

## Créer un modèle et gérer la migration associée à ce modèle 
php artisan make:model Course -m

## Les relations entre modèles

## One to One 
Relation la plus simple : un modèle qui appartient et fait référence à un autre modèle 

## One to Many 
Relation plus complexe, fait intervenir plus d'éléments (un post sera lié à plusieurs commentaires : entre 0 et plusieurs commentaire et 1 commentaire va appartenir à un seul post, la relation est différente dans les deux sens : un commentaire appartient à un seul post et un post peut avoir entre 0 et plusieurs commentaires, on aura un post_id dans la table "Comment", à partir du commentaire, on pourra directement retrouver le post grâce au post_id, plusieurs commentaires pourront avoir le même post_id).

## Many to Many 
La plus complexe : elle va nécessiter une table de relation entre les deux modèles concernés par la relation (un utilisateur peut avoir plusieurs rôles, on ne sait pas préciser ni dans rôle, ni dans user, le user_id directement, il ne fera référence qu'à un seul user. On aura donc une table role user qui fera la relation entre les deux modèles User et Role et qui va contenir pour chaque user_id, le rôle en question, cette table ne contiendra que des id pour faciliter la mise en place de la relation). Laravel propose, grâce à ses relations, de mettre en place des propriétés pour récupérer un modèle depuis un autre modèle.

## Faire un lien entre "storage" et "app/public" (connecter les deux dossiers)
## Résolution du souciss : https://www.it-swarm.dev/fr/php/stockage-dans-laravel-dit-lien-symbolique-aucun-fichier-de-ce-type/835197221/
php artisan storage:link 

## Installation du package pour récupérer les informations de la vidéo 
composer require james-heinrich/getid3

## bundle pour faire un panier
https://github.com/darryldecode/laravelshoppingcart/blob/master/src/Darryldecode/Cart/Cart.php

## Installation et configuration 
https://packagist.org/packages/darryldecode/cart

## Stripe 
https://dashboard.stripe.com/login

cassanogabriele78@gmail.com
Intheclawsofawitch1978

composer require stripe/stripe-php

Documentation : https://stripe.com/docs/stripe-js
Utilisation : https://github.com/stripe/stripe-php

## API (Application Programming Interface)
Elle va permettre à deux applications de communiquer entre elles : on communiquera depuis l'application Laravel avec Udemy pour récupérer des informations. Une API, expose, rend disponible des fonctionnalités ou des données. Pour pouvoir les utiliser, la plupart des API requièrent une clé (API Key), voir parfois deux. Cette clé va permettre à l'API d'identifier comme étant utilisateur et avoir les droits pour se servir de cet API.

https://www.udemy.com/instructor/account/api/

Aller à "Clients API" et il faut faire une demande de clé en cliquant sur le bouton "Demander un client API affilié".

Email envoyé car pas moyen de créer la clé API pour continuer la formation, le formulaire bloque au champs nom, j'ai beau essayé avec n'importe quoi, rien à faire.

## Déployer l'application sur Firebase 
On va pouvoir déployer l'application sur Firebase, c'est là que CLI va être utile, on va déployer l'application en une seule commande, "firebase deploy". Une fois que la commande a finit d'être exécuté, l'application est en ligne directement, l'adresse par défaut pour accéder au site est "https://nom_projet.firebaseapp.com". On peut même demander à Firebase d'afficher le site à notre place dans une navigateur, avec la commande "firebase open". Descendre et appuyer sur "Hosting: Deployed Site". Fibase ouvre la dernière application qu'on a déployé avec Firebase CLI, l'application est maintenant disponible en ligne à une adresse accesssible par tout le monde. Si on le souhaite, Firebase propose d'associer un autre nom domaine à l'application si celui donné par défaut ne nous convient pas. Si on utilise Chrome et que l'extension "ad block" est activée, il se peut que l'application affiche une simple page blanche, celui est du à l'extension "ad block" de Chrome et la librairie "zone js" requise pour faire fonctionner Angular. Pour remédier à ce problème "ad block" du navigateur, on a pas besoin de cette extension pour le site puisqu'il n'affiche pas de publicité.



