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

##################################################################################################################################################################

## Exécuter directement du code PHP (shell -> exit pour quitter)
php artisan tinker

## Récupérer toutes les catégories 
App\Category::all();

## Récupérer une catégorie aléatoire
App\Category::all()->random(1)->first->id;

######################################################################################################################################################################

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

## Angular et ECMAScript 6

## ECMAScript 6 ?

ECMAScript 6 est le nom de la dernière version standardisé de JavaScript. 
Si vous utilisez JavaScript pour vos développements, vous avez sans doute remarquez que JavaScript est un language un peu à part. Il existe un système d'héritage "prototypal", des fonctions "anonymes" ... Le besoin d'une nouvelle standardisation s'est fait sentir pour fournir à JavaScript les moyens de développer des applications web robustes.
Cette standardisation a été approuvé par l'organisme de normalisation en Juin 2015 : cela signifie que ce standard va être supporté de plus en plus par les navigateurs dans les temps à venir. ECMAScript 6 a été annoncé pour la première fois en 2008, et bientôt il deviendra inévitable.
Pour votre information, ECMAScript6, ECMAScript 2015 et ES6 désignent la même chose. Nous utiliserons ES6 comme nom, car c'est le surnom le plus populaire.
A quoi sert ECMAScript 6 dans une application Angular ?
ES6, via sa nouvelle syntaxe, apporte plusieurs nouvelles évolutions à JavaScript. Voici les éléments les plus intéressants que nous utiliserons dans le cadre de ce cours.
PS: Pas besoin de tout retenir, survolez simplement la liste ci-dessous pour vous familiariser avec la syntaxe de ES6.
Les classes
ES6 introduit une nouvelle syntaxe: le mot-clef class. C'est le même mot clé que dans d'autres langages, mais sachez que c'est toujours de l'héritage par prototype qui tourne derrière, mais vous n'avez plus à vous en soucier.

```
class Vehicule {
 constructor(couleur, nombreRoueMotrice) {
    this.couleur = couleur;    
    this.nombreRoueMotrice = nombreRoueMotrice;    
    this.moteurAllumer = false;    
 }

demarrer() {
  this.moteurAllumer = true;
}

couperMoteur() {
   this.moteurAllumer = false;
 }
}
```
Voilà une classe JavaScript, bien différente de ce que l'on avait précédemment. Si vous avez bien remarqué, on a même droit à un constructeur. C’est pas mal pour du JavaScript ! :)
Le nouveau mot-clef let
Le mot-clé let permet de déclarer une variable locale, dans le contexte où elle a été assignée. (Un contexte est le terme français pour désigner un le $scope dans AngularJS, ou scope en anglais). 
Par exemple, les instructions que vous écrivez dans le corps d'une fonction ou à l'extérieur n'ont pas le même contexte. Normalement une instruction if n'a pas de contexte en soi, mais maintenant si, avec le mot clé let. Cela peut être utile quand on veut effectuer beaucoup d'opérations sur une variable et que vous ne voulez pas polluer d'autres contextes des variables qui ne sont pas nécessaires dans d'autres contextes : 

```
var x = 1;

if(x < 10) { 
 let v = 1; 
 v = v + 21;
 console.log(v);
}

console.log(v); // v n'est pas définie, car v a été déclaré avec 'let' et non 'var'.
```

•  En général, garder un contexte global propre est vivement conseillé, et c'est pourquoi ce mot clé let est vraiment le bienvenu ! Sachez que let a été pensé pour remplacer var, alors nous n'allons pas nous en priver dans ce cours.
Le nouveau mot-clef const
•  Le mot clé const quant à lui, permet de déclarer ... des constantes ! Voyons comment cela fonctionne: 
•  const PI = 3.141592 ; 
•  Une déclaration de constante ne peut se faire qu'une fois, une fois définie, vous ne pouvez plus changer sa valeur.
•  C'est bien pratique si vous avez besoin de définir des valeurs une bonne fois pour toutes dans votre application.
•  Attention, le comportement est un peu différent pour une constante de tableau ou d'objet. Vous ne pouvez pas modifier la référence vers le tableau ou l'objet, mais vous pouvez continuer à modifier les valeurs à l'intérieur tableau, ou les propriétés de l'objet. 
Les fonctions fléchées
•  Les fonctions fléchées, ou arrow functions, ne sont pas des fonctions classiques, parce qu’elles ne définissent pas un nouveau contexte comme les fonctions traditionnelles. Nous les utiliserons beaucoup dans le cadre de la programmation asynchrone qui nécessite beaucoup de fonctions anonymes. 
•  La structure d'une fonction fléchée est toujours la même: (paramètre) => { corps de la fonction }. 
•  La fonction suivante:
```
bouton.onclick = function() {
  envoyerMail(this.email);
}
```
•  Correspond donc à la fonction fléchée suivante:
•  bouton.onclick = () => { envoyerEmail(this.email); } 
•  Je vous conseille de vous habituer dès maintenant à cette nouvelle syntaxe, et nous allons l'utiliser tout le temps ! 
Les paramètres de fonctions par défaut
•  En JavaScript ES6, on peut définir facilement des paramètres de fonctions avec une valeur par défaut.
•  Imaginons une fonction qui multiplie deux nombres passés en paramètres, mais le deuxième paramètre est facultatif, et il vaut 1 par défaut: 

```
function multiplier(a, b = 1) {
 return a * b;
}
```

•  Avec ES6, il suffit de définir une valeur par défaut dans la signature même de la fonction. C'est très pratique ! 
La syntaxe template string
•  La concaténation de chaîne de caractère a toujours été pénible avec JavaScript.
Mais avec ES6, on peut utiliser des templates strings, qui commencent et se terminent par un backtick. Il s'agit d'un symbole particulier qui permet d'insérer facilement des variables dans des chaînes de caractères. On peut insérer des variables dans la chaîne de caractères avec ${variable}, comme ceci:

```
let name = 'toto';
let email = 'toto@gmail.com';
console.info(‘${name} a pour email: ${email}’);
```

•  C'est quand même plus pratique que de concaténer des chaines de caractères entre elles !

## Conclusion
Nous avons vu plusieurs changements majeurs apporté par ES6 à Javascript. Sachez que ES6 est rétro-compatible, donc vous pouvez toujours continuer à développer de la façon dont vous le faites actuellement, puis migrer petit à petit vers la syntaxe d'ES6. Je vous recommande d'adopter ES6 assez rapidement, vous gagnerez en productivité et en lisibilité avec cette nouvelle syntaxe. 

Même si les nouveautés de ES6 ne fonctionnent pas encore dans certains navigateurs, beaucoup de développeurs ont commencé à développer avec ES6 et utilisent un transpilateur pour convertir leur code ES6 en du code ES5. Ainsi leur code est lisible par tout les navigateurs.
Un transpilateur est un outil qui permet de publier son code pour les navigateurs qui ne supportent pas encore l'ES6: le rôle du transpilateur est de traduire le code ES6 en code ES5. Comme certaines fonctionnalités d'ES6 ne sont pas disponibles avec ES5, leur comportement est simulé pour permettre aux navigateurs plus anciens de comprendre le code.

Dans la prochaine session, nous verrons que TypeScript permet de transpiler notre code ES6 en ES5, et ajoute une surcouche intéressante au JavaScript afin de pouvoir typer nos variables JavaScript. Et ça, c'est assez nouveau dans le monde du JavaScript !

## Angular et TypeScript

## C'est quoi, TypeScript ?

Nous allons aborder un des piliers d'Angular : TypeScript. Certains d'entre vous en ont peut-être déjà entendu parler, mais les autres ne vous en faites pas, nous allons démystifier tout cela immédiatement !
Avant de voir plus en détail ce que nous allons faire avec ce langage, et parce que je ne suis pas toujours inspiré, je vous propose de commencer par la définition de 

## Wikipédia

TypeScript est un langage de programmation libre et open-source, développé par Microsoft, qui a pour but d'améliorer et de sécuriser la production de code JavaScript. C'est un sur-ensemble de JavaScript (c'est-à-dire que tout code Javascript correct peut être utilisé avec TypeScript). Le code TypeScript est transcompilé en JavaScript, pouvant ainsi être interprété par n'importe quel navigateur web ou moteur JavaScript.
Je n'aurai pas été plus clair. Mais je vous rassure on va creuser tout ça tout de suite, je ne vais pas vous laisser avec une simple définition de Wikipédia. 
Les faiblesses du langage JavaScript font que lorsque l'on commence à écrire beaucoup de code, on arrive vite à un moment où on s'emmêle les pinceaux ! Notre code devient redondant, perd en élégance, et devient de moins en moins lisible : on parle de code spaghetti. Vous comprendrez tous seuls la référence aux célèbres pâtes italiennes ! ;)
La communauté des développeurs, ainsi que certaines entreprises, se sont mis alors à développer des méta-langages pour améliorer JavaScript : CoffeeJS, Dart et TypeScript en sont les exemples les plus réussis. Ces outils apportent également de nouvelles fonctionnalités qui font défaut au JavaScript natif, avec une nouvelle syntaxe moins verbeuse. 
TypeScript permet de typer nos variables, ce qui permet d'écrire du code plus robuste. Une fois que vous avez développé votre application, vous devez le compiler, c'est-à-dire le transformer en du code JavaScript que le navigateur pourra interpréter. En effet, votre navigateur ne sait pas interpréter le TypeScript. Vous devez d'abord compilez ce code en JavaScript pour qu'il soit lisible par votre navigateur.
Attention, l'extension des fichiers TypeScript est .ts et non .js !
A quoi sert TypeScript dans une application Angular ?
Il est chaudement recommandé d'utiliser TypeScript pour développer en Angular.  C'est ce que Google recommande explicitement dans la documentation officielle d'Angular.
En bonus, Angular lui-même est développer avec TypeScript. C'est pour cela que nous utiliserons TypeScript dans ce cours !
Le typage avec TypeScript
Voici comment typer nos variables avec TypeScript:

```
var pointDeVie: number = 100; 
var surnom: string = 'Green Lantern'; 
```

Comme vous pouvez le constater, il suffit d'ajouter deux points et le type de votre variable pour typer une variable en TypeScript. J'ai jouté en ressource la liste de tous les types de base disponibles avec TypeScript.
TypeScript et les fonctions
On peut aussi typer les paramètres et la valeur de retour d'une fonction, toujours avec la syntaxe des deux points:

```
function creerHeros(pointDeVie: number, surnom: string): Heros {
  var heros = new Heros(); 
  heros.pointDeVie = pointDeVie; 
  heros.surnom = surnom; 
  return heros; 
}
```

## Les décorateurs

Les annotations TypeScript permettent d'ajouter des informations sur nos classes, pour indiquer par exemple que telle classe est un composant de l'application, ou telle autre un service. On utilise @ comme syntaxe:

```
@Component({
 selector: 'mon-composant',
 template: 'mon-template.html'
})

export class MonComposant {}
```
On utilisera beaucoup cette syntaxe lors de nos développements avec Angular.

## Conclusion

TypeScript apporte évidemment d'autres fonctionnalités : les valeurs énumérées, les interfaces, la généricité, etc.
TypeScript est donc un méta-langage qui est surtout connu pour apporter le typage à JavaScript, mais il s'agit également d'un transpilateur, capable de générer du code vers ES5 ou ES6 !
L'objectif de cette section était que vous preniez rapidement connaissance de TypeScript, pour voir ensuite son fonctionnement concret dans une application Angular. Si vous voulez pousser plus loin vos connaissances en TypeScript, je vous invite à regarder la documentation officielle que j'ai ajouté en ressource de cette session.
Angular et les Composants Web

## C'est quoi, les Web Components ?

Les Web Components désignent un standard qui permet aux développeurs de créer des sections complètement autonomes au sein de leurs pages web. On peut par exemple créer un composant web qui gère l'affichage d'articles dans notre application: ce composant web fonctionnera indépendamment du reste de la page, il possèdera son propre code HTML, son propre code CSS et son propre code JavaScript, encapsulé dans le composant web. Il faudra ensuite insérer ce composant web dans la page principale de notre application pour indiquer que, à tel endroit, nous voulons afficher des articles grâce à ce composant web.
On peut voir les Web Components comme des widgets réutilisables.
Angular et les Web Components
Les Web Components utilisent des capacités standards, nouvelles ou en cours de développements, des navigateurs. Il s'agit de technologies récentes qui ne sont pas encore supportées par tous les navigateurs. Pour les utiliser dès aujourd'hui, nous devrons utiliser des polyfills pour combler les lacunes de couverture des navigateurs.
Un polyfill est un ensemble de fonction, souvent sous forme de scripts JavaScript, permettant de simuler sur un navigateur web ancien des fonctionnalités qui ne sont pas nativement disponibles.
Les Web Components sont composés de quatre technologies différentes, qui peuvent chacune être utilisées séparément, mais qui une fois assemblées forme le standard des Web Components :

1.	Les éléments personnalisés (Custom Elements) permettent de créer ses propres éléments HTML valides.
2.	Le DOM de l'ombre (Shadow DOM) permet d'encapsuler du code HTML, CSS et JavaScript qui n'interfère pas avec le DOM principal de la page web.
3.	Les templates HTML (HTML Templates) permettent de développer des morceaux de code HTML qui ne sont pas interprétés au chargement de la page.
4.	Les imports HTML (HTML Imports) permettent d'importer du HTML dans une autre page HTML.

Pour ceux qui ne s'en souviennent plus, le DOM est une représentation de votre code HTML sous forme d'arbre. Ainsi un élément <ul>  a des éléments fils <li> . L'élément racine du DOM est donc la balise <html> .
	
## Conclusion

Je ne vais pas vous présenter chacune de ces technologies pour le moment, le plus important est que vous compreniez pourquoi telle ou telle technologie a été créer, et à quoi elle sert. Retenez que les composants web permettent d'encapsuler une partie de votre page dans un composant, et que les composants Angular repose sur ce standard des Composants Web.

## En résumé

1.	Les sites web deviennent de plus en plus de véritables applications, et une utilisation intensive du langage JavaScript devient nécessaire.
2.	Angular est un Framework orienté composant, car votre application entière est un assemblage de composants.
3.	Angular est conçu pour le web de demain et intègre déjà la norme ECMAScript6 (ou ES6) et les Web Components.
4.	Enfin, retenez que tout cet écosystème est bourgeonnant et change (très) vite. Soyez persévérant lors de votre apprentissage et ne vous découragez pas. Vous prendrez vite plaisir à utiliser Angular !

## Avant de continuer : Angular 6

Dans la suite de ce cours, tous les extraits de code et la correction de l'application sont à jour pour Angular 6.
Cependant, la plupart des vidéos ont été tournées pour la version 5 d'Angular. Il y a donc quelques vidéos dans la session Premiers pas avec Angular et Effectuer des requêtes HTTP où j'utilise du code adapté uniquement pour la version 5 d'Angular. 
Je vous invite donc simplement à récupérer la version plus récente des fichiers concernés, qui sont indiqués en ressource de chaque vidéo de la formation. Je mettrai prochainement les vidéos concernées à jour, et je vous tiendrai informé grâce aux annonces Udemy.

## Installer NodeJS et NPM

Pour installer les dépendances de notre projet Angular que nous avons renseigné dans le fichier package.json, nous allons utiliser un petit outil bien pratique pour cela, nommé NPM (Node Package Manager).
Pour cela, il est nécessaire d'installer NodeJS, qui permet d'exécuter du code javaScript côté serveur. NodeJS ne nous sert pas directement dans cette formation, mais il permet d'installer NPM, qui va nous permettre d'exécuter des commandes "npm ..." sur notre machine. 

Voici le lien pour télécharger NodeJS sur Windows, Mac ou Linux :

👉 https://nodejs.org/fr/download
Dès que l'installation est terminée sur votre poste, vous êtes prêt à passer à la suite !
Cas où votre application ne démarre pas
Si l'application ne démarre pas...
Si votre application ne démarre pas correctement lorsque vous lancer la commande npm start, essayez les solutions suivantes :
- Placer le fichier main.ts dans le dossier src.
- Vérifier votre fichier package.json.
- Supprimer le dossier node_modules, et réinstaller vos dépendances avec la commande npm install.
- Lancer la commande npm run build:watch, puis dans un autre terminal, lancer la commande npm run serve.
J'espère que cela corrigera votre erreur. 
Si ça n'est toujours pas le cas, vous pouvez récupérer la correction dans les ressources de la correction. Ensuite lancez les commandes npm install et npm start, et vous devriez avoir un environnement de travail prêt pour continuer la formation. :)

## En résumé

1.	SystemJS est la bibliothèque par défaut choisie par Angular pour charger les modules.
2.	On a besoin au minimum d'un module racine et d'un composant racine par application.
3.	Le module racine se nomme par convention AppModule.
4.	Le composant racine se nomme par convention AppComponent.
5.	L'ordre de chargement de l'application est le suivant : index.html > main.ts > app.module.ts > app.component.ts.
6.	Le fichier package.json initial est fourni avec des commandes prêtes à l'emploi comme la commande npm start, qui nous permet de démarrer notre application web.

## Les cycles de vie d'un composant 

Chaque composant a un cycle de vie géré par Angular lui-même. Angular crée le composant, s'occupe de l'afficher, crée et affiche ses composants fils, vérifie quand les données des propriétés changent, et détruit les composants, avant de les retirer du DOM quand cela est nécessaire. Pratique, non ?
Angular nous offre la possibilité d'agir sur ces moments clefs quand ils se produisent, en implémentant une ou plusieurs interfaces, pour chacun des événements disponibles. Ces interfaces sont disponibles dans la librairie core d'Angular. 
Chaque interface permettant d'interagir sur le cycle de vie d'un composant fournit une et une seule méthode, dont le nom est le nom de l'interface préfixé par ng. Par exemple, l'interface OnInit fournit la méthode ngOnInit, et permet de définir un comportement lorsque le composant est initialisé. 
Voici ci-dessous la liste des méthodes disponibles pour interagir avec le cycle de vie d'un composant, dans l'ordre chronologique du moment où elles sont appelées par Angular.

1. ngOnChanges: C'est la méthode appelée en premier lors de la création d'un composant, avant même ngOnInit, et à chaque fois que Angular détecte que les valeurs d'une propriété du composant sont modifiées. La méthode reçoit en paramètre un objet représentant les valeurs actuelles et les valeurs précédentes disponibles pour ce composant. 
2. ngOnInit: Cette méthode est appelée juste après le premier appel à ngOnChanges, et elle initialise le composant après qu’Angular ait initialisé les propriétés du composant. 
3. ngDoCheck: On peut implémenter cette interface pour étendre le comportement par défaut de la méthode ngOnChanges, afin de pouvoir détecter et agir sur des changements qu’Angular ne peut pas détecter par lui-même. 
4. ngAfterViewInit: Cette méthode est appelée juste après la mise en place de la vue d'un composant, et des vues de ses composants fils s'il en a.
5. ngOnDestroy: Appelée en dernier, cette méthode est appelée avant qu’Angular ne détruise et ne retire du DOM le composant. Cela peut se produire lorsqu'un utilisateur navigue d'un composant à un autre par exemple. Afin d'éviter les fuites de mémoire, c'est dans cette méthode que nous effectuerons un certain nombre d'opérations afin de laisser l'application "propre" (nous détacherons les gestionnaires d'événements par exemple). 

Même si vous ne définissez pas explicitement des méthodes de cycle de vie dans votre composant, sachez que ces méthodes sont appelées en interne par Angular pour chaque composant. Lorsqu'on utilise ces méthodes, on vient donc juste surcharger tel ou tel événement du cycle de vie d'un composant. 

Les méthodes que vous utiliserez le plus seront certainement ngOnInit et ngOnDestroy, qui permettent d'initialiser un composant, et de le nettoyer proprement par la suite lorsqu'il est détruit. 

Cas où votre application ne démarre pas :

Si l'application ne démarre pas...
Si votre application ne démarre pas correctement lorsque vous lancer la commande npm start, essayez les solutions suivantes :
- Placer le fichier main.ts dans le dossier src.
- Vérifier votre fichier package.json.
- Supprimer le dossier node_modules, et réinstaller vos dépendances avec la commande npm install.
- Lancer la commande npm run build:watch, puis dans un autre terminal, lancer la commande npm run serve.
J'espère que cela corrigera votre erreur. 
Si ça n'est toujours pas le cas, vous pouvez récupérer la correction dans les ressources de la correction. Ensuite lancez les commandes npm install et npm start, et vous devriez avoir un environnement de travail prêt pour continuer la formation. :)

## En résumé

1.	SystemJS est la bibliothèque par défaut choisie par Angular pour charger les modules.
2.	On a besoin au minimum d'un module racine et d'un composant racine par application.
3.	Le module racine se nomme par convention AppModule.
4.	Le composant racine se nomme par convention AppComponent.
5.	L'ordre de chargement de l'application est le suivant : index.html > main.ts > app.module.ts > app.component.ts.
6.	Le fichier package.json initial est fourni avec des commandes prêtes à l'emploi comme la commande npm start, qui nous permet de démarrer notre application web.

## Les cycles de vie d'un composant 

Chaque composant a un cycle de vie géré par Angular lui-même. Angular crée le composant, s'occupe de l'afficher, crée et affiche ses composants fils, vérifie quand les données des propriétés changent, et détruit les composants, avant de les retirer du DOM quand cela est nécessaire. Pratique, non ?
Angular nous offre la possibilité d'agir sur ces moments clefs quand ils se produisent, en implémentant une ou plusieurs interfaces, pour chacun des événements disponibles. Ces interfaces sont disponibles dans la librairie core d'Angular. 
Chaque interface permettant d'interagir sur le cycle de vie d'un composant fournit une et une seule méthode, dont le nom est le nom de l'interface préfixé par ng. Par exemple, l'interface OnInit fournit la méthode ngOnInit, et permet de définir un comportement lorsque le composant est initialisé. 
Voici ci-dessous la liste des méthodes disponibles pour interagir avec le cycle de vie d'un composant, dans l'ordre chronologique du moment où elles sont appelées par Angular.

1. ngOnChanges: C'est la méthode appelée en premier lors de la création d'un composant, avant même ngOnInit, et à chaque fois que Angular détecte que les valeurs d'une propriété du composant sont modifiées. La méthode reçoit en paramètre un objet représentant les valeurs actuelles et les valeurs précédentes disponibles pour ce composant. 
2. ngOnInit: Cette méthode est appelée juste après le premier appel à ngOnChanges, et elle initialise le composant après qu’Angular ait initialisé les propriétés du composant. 
3. ngDoCheck: On peut implémenter cette interface pour étendre le comportement par défaut de la méthode ngOnChanges, afin de pouvoir détecter et agir sur des changements qu’Angular ne peut pas détecter par lui-même. 
4. ngAfterViewInit: Cette méthode est appelée juste après la mise en place de la vue d'un composant, et des vues de ses composants fils s'il en a.
5. ngOnDestroy: Appelée en dernier, cette méthode est appelée avant qu’Angular ne détruise et ne retire du DOM le composant. Cela peut se produire lorsqu'un utilisateur navigue d'un composant à un autre par exemple. Afin d'éviter les fuites de mémoire, c'est dans cette méthode que nous effectuerons un certain nombre d'opérations afin de laisser l'application "propre" (nous détacherons les gestionnaires d'événements par exemple). 

Même si vous ne définissez pas explicitement des méthodes de cycle de vie dans votre composant, sachez que ces méthodes sont appelées en interne par Angular pour chaque composant. Lorsqu'on utilise ces méthodes, on vient donc juste surcharger tel ou tel événement du cycle de vie d'un composant. 

Les méthodes que vous utiliserez le plus seront certainement ngOnInit et ngOnDestroy, qui permettent d'initialiser un composant, et de le nettoyer proprement par la suite lorsqu'il est détruit. 

## Les données

Maintenant, créons un fichier mock-pokemons.ts qui contiendra les données de plusieurs Pokémons. Ce fichier doit être placé dans le dossier src/app (le fichier est un peu long, mais il s'agit simplement de données mises à disposition pour notre application). Etant donné que nous n’allons pas modifier ce fichier dans la suite du cours, je vous propose de le copier directement à partir de l’adresse suivante.
Comme vous pouvez le constater, ce fichier ne fait qu'exporter la constante POKEMONS, qui contient des données nécessaires pour notre application.
Maintenant, vous avez tous les éléments nécessaires pour améliorer le composant app.component.ts de notre application. Pour rappel, voici ce que vous devez faire :

1. Injecter une liste de Pokémons dans le composant. 
2. Préparer une méthode qui devra gérer l'action lorsque l'utilisateur cliquera sur un Pokémon de cette liste.
A vous de jouer maintenant !
Syntaxe de liaison des données
Syntaxe de liaison des données
L'interpolation est très pratique pour lier notre template et notre composant. Cependant, il existe d'autres manières de créer des liaisons entre le composant et le template. L'interpolation a une particularité : elle pousse les données depuis le composant vers le template, mais ce n'est pas le seul moyen de faire. Nous allons voir les autres types de liaisons possibles.
Du composant vers le template
Nous pouvons pousser plusieurs données depuis le composant vers le template. Voici les liaisons que nous pouvons mettre en place :
La liaison sur une propriété d'élément
On utilise les crochets pour lier directement la source de l'image à la propriété someImageUrl du composant : 
```<img [src]="someImageUrl"> ```
La liaison sur une propriété d'attribut
On lie l'attribut for de l'élément label avec la propriété de notre composant someLabelId :
```<label [attr.for]="someLabelId">...</label>``` 
La liaison sur une propriété de la classe
Fonctionnement similaire, pour attribuer ou non la classe special à l'élément div ci-dessous :
```<div [class.special]="isSpecial">Special</div> ```
La liaison sur une propriété de style
On peut également définir un style pour nos éléments de manière dynamique : ici on définit la couleur de notre bouton en fonction de la propriété isSpecial, soit rouge, soit vert. C'est un opérateur ternaire que l'on utilise comme expression :
```<button [style.color]="isSpecial ? 'red' : 'green'"> ```

## En résumé

1. L'interpolation permet d'afficher les propriétés de nos composants dans les templates, via la syntaxe {{ }}.
2. On peut lier une propriété d'élément, d'attribut, de classe ou de style d'un composant vers le template.
3. Si nos templates sont trop long, on peut utiliser le backtick d'ES6, ou définir nos templates dans des fichiers séparés.
4. La directive NgIf permet de conditionner l'affichage d'un template.
5. La directive NgFor permet d'afficher une propriété de type tableau dans un template.
6. On peut gérer les interactions d'un utilisateur avec un élément de la page grâce à la syntaxe : '(' + 'nom de l'événement' + ')'.
7. On peut référencer des variables directement dans le template plutôt que de manipuler l'objet $event.
8. Les variables référencées dans le template sont accessibles pour tous les éléments fils et frères de l'élément dans lequel elle ont été déclarées.
9. Essayez d'éviter de mettre la logique de votre application dans vos templates. Gardez-les le plus simple possible !

## En résumé

1. On utilise l'annotation @Directive pour déclarer une directive dans notre application.
2. Il existe trois types de directives différentes : les composants, les directives d'attributs et les directives structurelles (ngFor et ngIf par exemple).
3. Une directive d'attribut permet d'agir avec les éléments HTML d'une page, en leur attachant un comportement spécifique.
4. Une directive utilise un sélecteur CSS pour cibler les éléments HTML sur lesquels elle s’applique.
5. Il est recommandé de préfixer le nom de ses directives pour éviter les problèmes de collisions.
6. Angular crée une nouvelle instance de notre directive à chaque fois qu'il détecte un élément HTML avec l'attribut correspondant. Il injecte alors dans le constructeur de la directive l'élément du DOM ElementRef.
7. Il faut déclarer notre directive pour pouvoir l’utiliser.
8. On utilise l'annotation @HostListener pour gérer les interactions de l'utilisateur au sein d'une directive.

## En résumé

1. Les pipes permettent de formater les données affichées dans nos templates.
2. L'opérateur des pipes est « | ».
3. Angular fournit des pipes prêts à l'emploi, disponibles dans tous les templates de notre application : DatePipe, UpperCasePipe, LowerCasePipe, etc.
4. Les pipes peuvent avoir des paramètres, mais tous les paramètres sont facultatifs.
5. On peut créer des pipes personnalisés pour les besoins de notre application avec l'annotation @Pipe.
6. Les pipes personnalisés doivent être déclarés avant de pouvoir être utilisés dans les templates de composants. 

## En résumé

1. Il existe deux types de modules : le module racine et les modules de fonctionnalité, appelés également sous-modules. 
2. On déclare un module avec l'annotation @NgModule, quel que soit le type du module. 
3. On peut créer des applications complexes en ajoutant des modules de fonctionnalité au module racine.
4. Chaque module regroupe tous les composants, directives, pipes, services, ... liés au développement d'une fonctionnalité donnée, dans un dossier à part.
5. Chaque module peut disposer de ses propres routes également. 
6. On définit les routes de nos sous-modules avec forChild, et forRoot pour le module racine.
7. Modifier l'architecture d'une application existante peut être pénible, il est préférable de prévoir l'architecture des modules de votre application à l'avance. 

## En résumé

1. Il faut ajouter l'annotation @Injectable sur tous nos services.
2. Un service permet de factoriser et de centraliser du code qui peut être utile ailleurs dans l'application.
3. On utilise l'injection de dépendances pour rendre un service disponible dans un composant.
4. On ne gère jamais nous-mêmes les dépendances sur un composant ou un service, on passe toujours par l'injection de dépendances.
5. L'injection de dépendance permet de garantir que l'instance de notre service est unique à travers toute l'application.
6. On définit un fournisseur de service pour déterminer dans quelles zones de notre application notre service sera disponible.
7. On peut fournir un service pour toute l'application, pour un module particulier ou pour un composant. 

## En résumé

1. Il y a deux modules différents pour développer des formulaires avec Angular: FormsModule et ReactiveFormsModule. 
2. Le module FormsModule est pratique pour développer des formulaires de petites tailles, et met à disposition les directives NgForm et NgModel. 
3. La directive NgModel ajoute et retire certaines classes au champ sur lequel elle s'applique. Ces classes peuvent être utilisées pour afficher des messages d'erreurs ou de succès, et des indicateurs visuels. 
4.La syntaxe à retenir pour utiliser NgModel est [()]. 
5. On peut utiliser les attributs HMTL5 pour gérer la validation côté client, comme required ou pattern.
6. On peut utiliser des validateurs personnalisés en développant ses propres méthodes de validation.
7. Il faut toujours effectuer une validation côté serveur en complément de la validation côté client, si vous avez prévu de stocker des données depuis votre application.

## En résumé

1. Les promesses sont natives en JavaScript depuis l'arrivée de la norme ES6.
2. La programmation réactive implique de gérer des flux de données asynchrones.
3. Un flux est une séquence d'événements ordonnés dans le temps.
4. On peut appliquer différentes opérations sur les flux : regroupements, filtrages, troncatures, etc.
5. Un flux peut émettre trois types de réponses : la valeur associée à un événement, une erreur, ou un point de terminaison pour mettre fin au flux.
6. La librairie RxJS est la librairie la plus populaire pour implémenter la programmation réactive en JavaScript.
7. Dans RxJS, les flux d'événements sont représentés par un objet appelé Observable. 

## Installation d'un module permettant de simuler une API Web

Avant de continuer ce cours, nous devons nous assurer que nous disposons du paquet angular-in-memory-web-api dans notre application. C'est un paquet que nous utiliserons dans la prochaine session, afin de simuler une API Web au sein de notre application.
Pour commencer, vérifiez que votre fichier package.json contient la ligne de code suivante:
"angular-in-memory-web-api": "^0.6.0",
Si ça n'est pas le cas, vous devez installer ce paquet via la commande suivante: 
npm install --save-dev angular-in-memory-web-api
(L'option --save-dev permet de sauvegarder ce paquet directement dans la section devDependencies de votre fichier package.json)
Une fois la commande exécutée (ou alors si vous disposez déjà du fichier package.json à jour), vous pouvez continuer le cours sereinement.

## Modification de l'importation de l'opérateur "of"

Comme vu précédemment, remplacer l'importation de l'opérateur "of" du fichier pokemons.service.ts: 
import { of } from 'rxjs/observable/of'; // RxJS 5, importation dépréciée.
Par la nouvelle importation :
import { of } from 'rxjs'; // RxJS 6, à utiliser.

## En résumé

1. Il est possible de mettre en place une API web de démonstration au sein de votre application. Cela vous permettra d'interagir avec un jeu de données configuré à l'avance.
2. Les Observables permettent de faciliter la gestion des événements asynchrones.
3. Les Observables sont adaptés pour gérer des séquences d'événements.
4. Les opérateurs RxJS ne sont pas tous disponibles dans Angular. Il faut étendre cette implémentation en important nous-même les opérateurs nécessaires.

## En résumé

1. L'authentification nécessite la mise en place d'un système fiable: on utilise pour cela les Guards.
2. Les Guards permettent de gérer toutes sortes de scénarios liés à la navigation: redirection, connexion, etc.
3. Les Guards reposent sur un mécanisme simple. Ils retournent un booléen de manière synchrone ou asynchrone, qui permet d'influencer le processus de navigation.
4. Il existe plusieurs types de Guards différents. Le type utilisé pour l'authentification est CanActivate.
5. Il faut toujours déclarer les Guards au niveau du module racine, ainsi que les services tiers qu'ils utilisent. 

## Fixer la version de la dépendance core-js

Lors de l'écriture et du tournage de ce cours, je dois vous avouer que j'ai commis une erreur. 
A la ligne 10, je vous ai demandé de modifier l'importation de core-js comme suit :
<script src="https://unpkg.com/core-js/client/shim.min.js"></script>
Le problème avec ce code, c'est que je n'ai pas figé cette dépendance au moment de l'écriture du cours. Comme cette dépendance a continué à évoluer par rapport à Angular, et bien à un moment il y a une incompatibilité entre les deux versions, et cela cause une erreur au démarrage de votre application.
Il faut donc fixer le paquet core-js en version 2.5.4 pour que votre application continue à fonctionner. Je vous invite donc à effectuer la modification suivante, à la ligne 10 de votre fichier index.html :
<script src="https://unpkg.com/core-js@2.5.4/client/shim.min.js"></script>
Désormais, votre application fonctionnera lorsque vous la déploierai.

## En résumé

1. Le déploiement est une étape dans un projet qui consiste à faire fonctionner une application sur l'environnement de production. 
2. Avant de déployer un projet local sur une machine de développement, il est nécessaire de prévoir une étape d'optimisation. 
3. Le site unpkg.com permet de charger des paquets npm depuis le web. 
4. Firebase propose un utilitaire en ligne de commande nommé Firebase-CLI, afin de déployer en ligne facilement des applications web statiques. Cela fonctionne aussi pour les applications web statiques qui ne sont pas développées avec Angular.
5. Je vous recommande de lire la documentation officielle pour mieux connaître toutes les optimisations possibles que vous pouvez faire en local, avant le déploiement.

## Introduction

Actuellement, nous sommes capables de définir un titre pour les pages de notre application, en ajoutant la balise <title> dans le fichier index.html. Cependant, notre application devrait être en mesure de modifier ce titre dynamiquement en fonction de la page qui est affichée à l'utilisateur. Nous allons voir dans cette session comment le faire.
Pour information, un des éléments de base de toute stratégie de référencement est l'optimisation de la balise <title> !
Le problème avec la balise <title>
La question qui se pose à nous est la suivante :
Comment définir dynamiquement un titre aux pages de notre application ?
L'approche la plus évidente serait à première vue d'utiliser l'interpolation pour lier une propriété du composant à la balise HTML <title>:
<title>{{ property_title_of_some_component }}</title> 
Malheureusement, cela ne marchera pas !
Et pourquoi pas ? C'est bien comme ça que l'on fait de l'interpolation, non ?
En fait, le problème n'est pas là. Le composant racine de votre application est un élément contenu à l'intérieur de la balise <body>. La balise HTML <title> est dans le document <head>, en dehors du corps, ce qui le rend inaccessible à la liaison de données Angular !
Nous pourrions récupérer l'objet du navigateur nommé document et définir le titre manuellement. Mais ce n'est pas très propre et compromet nos chances d'exécuter un jour l'application en dehors du navigateur.
NB: Pour rappel, vous n'êtes pas obligé d'exécuter votre application à l'intérieur d'un navigateur ! Vous pouvez développez des applications mobiles hybrides avec Ionic ou NativeScript. Vous pouvez également utiliser Electron.js ou Windows Universal pour développer des applications à destination des clients de bureaux lourds.

## Utiliser le service Title
Heureusement, Angular fournit un service nommé Title. Ce service est une simple classe, qui fournit deux méthodes pour récupérer et modifier le titre du document HTML courant.

1. getTitle() : string —Récupère le titre du document HTML courant.
2. setTitle(newTitle : string) — Définit un nouveau titre pour le document HTML courant.
La classe de ce service est disponible sur la documentation officielle.
Maintenant nous allons utiliser ce service Title. Il faut injecter le service dans le composant où l'on souhaite l'utiliser. Etant donné que ce service est appelé à être utilisé dans toute l'application, nous allons l'injecter dans le composant racine, AppComponent. Ensuite on peut définir un titre à la page, grâce à la méthode setTitle, à la ligne 5:

```
export class AppComponent implements OnInit {
 public constructor(private titleService: Title) {}
 ngOnInit() {
  this.titleService.setTitle("Mon Titre !");  
}
}
```

Il n'y a rien d'extraordinaire dans ce code. Nous utilisons le mécanisme classique d'injection de dépendance pour rendre le service disponible dans le composant.
Bien entendu, il faut également ajouter un fournisseur pour ce service, dans le module racine de notre application:
```
import { NgModule } from '@angular/core';
import { BrowserModule, Title } from '@angular/platform-browser'; // on importe le service 'Title'
import { AppComponent } from './app.component';

@NgModule({
  imports: [
   BrowserModule
],

declarations: [ AppComponent ],
 providers: [ 
  Title // on fournis le service 'Title' à l'ensemble de l'application 
],
bootstrap: [ AppComponent ]
})
export class AppModule { }
```
## Conclusion

Vous savez désormais comment définir des titres dynamiques pour vos pages. Vous pouvez proposer une expérience plus agréable à vos utilisateurs, en précisant le titre de la page sur laquelle ils se trouvent dans l'onglet du navigateur. J'espère que vous n'hésiterez pas à utiliser ce service dans vos projets !

## En résumé

1. Il n'est pas possible d'utiliser l'interpolation pour définir un titre à vos documents.
2. Angular fournit un service nommé Title pour déterminer dynamiquement un titre sur vos documents.
3. Ce service est une simple classe avec deux méthodes : une pour récupérer le titre de la page courante, et une autre pour le modifier.
4. On utilise ce service comme n'importe quel autre service, mais il est recommandé de le fournir au niveau du module racine, étant donné qu'il est destiné à servir au niveau globale de l'application.

## Introduction

Si vous travaillez dans une équipe de développeurs, vous avez remarqué que souvent chacun a ses petites habitudes. On n'arrive pas à se mettre d'accord sur le nom des variables à utiliser, le nom des fichiers, le nombre de fonctions qu'il faut développer... Bref, on aurait grand besoin d'un petit guide qui rassemble au même endroit toutes les bonnes pratiques de développement recommandées par la documentation officielle, avec des explications claires afin de mettre tout le monde d'accord !

Si vous êtes à la recherche de ce guide pour connaître la syntaxe, les conventions, et la meilleure structure possible pour développer une application Angular, vous êtes au bon endroit !

Le but de ce chapitre est de résumer les recommandations officielles, et voir pourquoi ce sont elles qui ont été retenues. Ensuite je vous présenterai deux outils pour vous permettre d'appliquer ces recommandations, sans avoir à relire tout votre code vous-même.
Il n'est pas important de connaître TOUTES les recommandations. Retenez juste celles qui sont les plus importantes pour vous et gardez-les dans un coin de votre tête pour vos futurs développements.

## Le principe de responsabilité unique

Il est recommandé d'appliquer ce principe à tous vos composants, vos services et autres éléments. Il permet de rendre votre application plus facile à lire, à maintenir et à tester.

## Règle 1

Définir un seul élément par fichier : un composant, un module ou un service, par exemple.
Le fait de définir un seul élément par fichier permet plusieurs choses :

1. Un unique élément par fichier le rend plus facile à lire et à maintenir, et évide les collisions avec les autres développeurs lorsque vous versionnez votre code.
2. Cela évite également d'avoir des variables qui peuvent être partagées entre deux composants dans le même fichier, ou autres couplages indésirables.

Essayer de limiter vos fichiers à 400 lignes. S'ils sont plus longs, c'est que vous avez probablement au moins deux éléments à l’intérieur.

## Règle 2

Définissez des petites fonctions plutôt que des fonctions trop importantes.
Les petites fonctions sont plus faciles à tester, à lire et à maintenir, et encouragent la réutilisation. Elles aident à éviter les bugs qui se produisent avec les fonctions trop importantes qui partagent des variables avec un contexte externe, ou des couplages indésirables avec les dépendances.
Essayer de limiter vos fonctions à 75 lignes.

## Les conventions de nommage

Les conventions de nommage sont importantes pour la cohésion de votre application. Nous allons voir que ces conventions s'appliquent aux noms des fichiers, et aussi aux noms des éléments eux-mêmes : composants, services, etc ...

## Règle 1

Utilisez des noms de fichiers consistants pour les éléments que vous définissez : feature.type.extension.
Les noms de fichiers list-pokemons.component.ts, list-pokemons.component.html ou encore pokemons.service.ts respectent cette recommandation. Cela permet aux développeurs d'avoir une idée sur le contenu du fichier en un coup d'oeil. Cela permet également d'avoir une certaine consistance sur les noms des fichiers de l'application, ce qui est primordial lorsqu'on travaille en équipe.

## Règle 2

Utilisez la syntaxe CamelCase pour nommer vos éléments, en suffixant leur nom avec leur type.
De cette manière, vous pourrez identifier rapidement les éléments de votre application. Le tableau ci-dessous illustre l'application de cette règle :

1. Le composant AppComponent => app.component.ts.
2. Le composant PokemonListComponent => pokemon-list.component.ts.
3. Le template de PokemonListComponent => pokemon-list.component.html.
4. La feuille de style de PokemonListComponent => pokemon-list.component.css.
5. La directive AwesomeDirective => awesome.directive.ts.
6. Le service PokemonsService => pokemons.service.ts.

## Règle 3

Utiliser la syntaxe kebab-case pour nommer les sélecteurs de vos directives.
Cette règle peut sembler évidente car les sélecteurs de vos directives seront liés aux attributs d'un élément HTML, qui ont des noms définis en minuscule. De plus, le parseur HTML d'Angular est sensible à la casse, donc vous n'avez pas le choix !
Règle 4
Utiliser un préfixe personnalisé pour les sélecteurs de vos composants et directives. Par exemple, le préfixe pa pour l'application Pokemon-App ou admin pour une zone dédiée aux fonctionnalités d'administration.

Préfixer les sélecteurs de vos composants et de vos directives ne coûte pas grand chose, et permet d'éviter les collisions dans votre application : 

```
@Component({
 selector: 'pa-pokemon'
})
export class PokemonComponent {}
 @Component({
 selector: 'admin-users'
})

export class UsersComponent {}
 @Directive({
 selector: '[paValidate]'
})
export class ValidateDirective {}
```

## Les conventions de code

## Règle 1

Déclarez des constantes plutôt que des variables si leur valeur ne doit pas changer, avec la syntaxe camelCase plutôt que UPPER_SNAKE_CASE.
Utiliser des constantes plutôt que des variables lorsque c'est nécessaire nous permet d'informer les autres développeurs que cette valeur est invariable. De plus, TypeScript nous aide en obligeant une initialisation immédiate et en empêchant une réaffectation ultérieure. La syntaxe camelCase a été retenue car elle est plus facile à lire que la syntaxe traditionnelle pour les constantes UPPER_SNAKE_CASE.
Cependant, on retrouve souvent dans les librairies tierces cette syntaxe traditionnelle, qui est encore très populaire. C'est pourquoi cette syntaxe est tolérée, même s'il est recommandé de déclarer vos constantes avec camelCase:

1. export const mockPokemons = ['Salamèche', 'Bulbizzare']; // préférable
2. export const pokemonsUrl = 'api/pokemons'; // préférable
3. export const POKEMONS_URL = 'api/pokemons'; // toléré

## Règle 2

Utilisez la syntaxe camelCase pour nommer vos propriétés et méthodes, et n'utilisez pas le préfixe underscore sur les propriétés privées !
TypeScript fait très bien la différence entre une méthode privée ou publique, de même pour les propriétés. Ne vous embêtez pas à ajouter des underscores partout !
Règle 3
Séparez par un espace les importations des librairies tierces de celles que vous avez codées vous-même.
La ligne vide vous permettra de rendre les importations plus faciles à lire et à localiser:
```
import { Component } from '@angular/core';
import { Http } from '@angular/http';
import { Pokemon } from './pokemon.model';
```
``` import { OneService, AnotherService, LastService } from '../../shared';```
	
## La structure de l'application

Même si vous venez juste de commencer le développement de votre projet, ayez une vision à long terme de la mise en oeuvre de votre application en suivant les recommandations ci-dessous, dès le départ de votre projet:

##Règle 1

LIFT : Localiser votre code rapidement, Identifier le code en un coup d'oeil, conserver la structure aussi Flat que possible (moins de sept fichiers pas dossier pour être plus exacte), et enfin « Try to be DRY ».
DRY signifie “Don't Repeat Yourself”. C'est un adage connu des développeurs, qui invite à la centralisation et à la réutilisation d'éléments déjà développés, afin d'éviter de répéter plusieurs fois le même code.
Définissez la structure de votre application en respectant ces grandes lignes directrices, indiqué ici par ordre d'importance. Cela vous permettra de garder une architecture cohé- rente lorsque votre application se développera. Cette architecture modulaire permet aux développeurs de se repérer rapidement dans leur code.
N'hésitez pas à créer un dossier par composant pour respecter le F de LIFT. Dans ce dossier, vous pourrez mettre le fichier TypeScript du composant, sa vue HTML, son style CSS et ses fichiers de tests éventuels.

## Règle 2

Mettez tous les fichiers partagés par un module dans un dossier partagé nommé shared.
N'hésitez pas à séparer les fichiers communs à plusieurs composants dans un dossier spécifique. Cela vous permettra de localiser plus rapidement les fichiers partagés. Vous pouvez créer deux types de dossier partagé:

1. Au niveau du dossier global app de votre application: vous pouvez définir y placer la barre de navigation, ou un service pour gérer les exceptions de votre application par exemple.
2. Au niveau des modules de fonctionnalités: par exemple dans le module des Pokémons, on pourrait placer le service pokemons.service.ts et le modèle pokemon.model.ts dans un dossier partagé.

## Règle 3

Il est possible de créer un fichier qui importe, agrège, et réexporte des éléments. Cette technique s'appelle le barrel et le fichier utilisé pour cela se nomme index.ts, par convention.
Un barrel permet agréger plusieurs importations en une seule, ce qui réduit le nombre d'importations que l'on peut déclarer dans un fichier. On a souvent recours à un barrel pour exporter tous les éléments d'un même dossier :

1. import {CONFIG, EntityService, ExceptionService, SpinnerService, ToastService} from '../shared';
Cette technique ne fonctionne que si le dossier shared contient un fichier index.ts avec le contenu suivant:
```
export * from './config';
export * from './entity.service';
export * from './exception.service';
export * from './filter-text';
export * from './init-caps.pipe';
export * from './modal';
export * from './nav';
export * from './spinner';
export * from './toast';
```
C'est assez pratique puisque nous n'avons plus qu'une ligne d'importation dans le reste de l'application !

## Les composants

## Règle 1
Utiliser la syntaxe kebab-case pour les sélecteurs de vos composants.
Cette syntaxe vous permet de préfixer plus facilement vos sélecteurs avec un espace de nom.

## Règle 2
Il faut extraire du composant les templates et la feuille de style du fichier quand ils font respectivement chacun plus de trois lignes.
De plus, vous devez nommer le template et les feuilles de style de la même manière que le composant, en changeant juste l'extension du fichier :

```[component-name].component.hml pour le template.```
```[component-name].component.css pour la feuille de style.```

## Règle 3

Déclarez les propriétés avant les méthodes dans un composant, et les éléments privés après ceux qui sont publics, par ordre alphabétique.
Il s'agit simplement d'une recommandation pour avoir une structure commune entre tous vos composants.

## Règle 4

Limiter la logique d'un composant aux seules nécessités de la vue. Toutes les autres logiques métiers doivent être déléguées dans des services.
La logique d'un composant pouvant être réutilisé par plusieurs composants doit être placée dans un service, afin d'éviter la redondance dans votre application. Vos composants doivent être uniquement concentrés sur la gestion de la vue, c'est leur rôle principal.
Pour rappel, évitez d'avoir de la logique métier à l'intérieur de votre template : déplacez-là au niveau de la classe du composant !

## Les services

## Règle 1

Utiliser les services comme des singletons, avec le même injecteur.
Lorsque vos services sont des singletons, il est plus simple de les utiliser pour partager des données ou des méthodes à travers un module en particulier, ou dans toute l'application.

## Règle 2

Fournissez les services à l'injecteur d'Angular au niveau du plus haut élément où ils seront partagés.
Cette règle est principalement due au fait que l'injecteur d'Angular est hiérarchique. Lorsque que l'on fournit un service au composant le plus élevé, cette instance du service est partagée et rendue disponible pour tous les composants fils !

## Règle 3

Séparer l'accès aux données dans un service.
La logique de votre application qui concerne les opérations et l'interaction avec des données distantes ou locales doit se faire dans un service dédié, à savoir : les appels XHR, l'accès au local storage, aux données en mémoire et autres...
Nous l'avons déjà vu : le rôle d'un composant est de recueillir et de présenter les données dans la vue. Il ne doit pas se préoccuper de la façon dont ces données sont obtenues, mais de la façon dont elles seront affichées dans la vue !

## Les outils à connaître

Les règles que nous venons de voir sembles intéressantes, et vous aimeriez sans doute les appliquer à votre code. 
Mais comment faire ?
Vous n'allez quand même pas relire tout le code de votre application, en vérifiant si chaque fichier respecte telle ou telle recommandation ! Ce serait très long, ennuyeux et inefficace.
Heureusement, la communauté des développeurs d'Angular propose deux outils différents:

1. Des outils de validation du code, qui permettent de vérifier que votre code respecte bien les bonnes pratiques de développement recommandées par Angular.
2. Des outils pour vous aider à développer du code valide (une sorte d'anticipation de la règle précédente).
Chacun de ces outils pourrait faire l'objet d'un chapitre entier, je vais simplement vous présenter leur fonction au sein d'un projet Angular, et pour la suite je fais confiance à votre curiosité.

## Vérifier la validité du code

L'outil recommandé pour vérifier si son code respecte les bonnes pratiques de développement est Codelyzer.
Cet outil s'occupe pour vous de vérifier l'ensemble de votre code, et de vous indiquer dans quel fichier vous avez omis de respecter une recommandation. Pour chaque oubli, Codelyzer vous fournit un lien vers la documentation officielle afin que vous puissiez voir par vous même quelle règle vous avez enfreint !
Il vous rédige une sorte de rapport sur l'état de votre application, et c'est ensuite à vous de décider si vous prenez en compte ses retours.
Cette vidéo illustre très bien ce qu'il est possible de faire avec Codelyzer.

## Accélérez vos développements

Lorsque vous développez, vous avez dû remarquer que vous effectuez souvent les mêmes tâches. Par exemple, quand vous créer un nouveau composant, il y a beaucoup de code commun à tous les composants. Vous devez importer l'annotation @Component, déclarer un sélecteur, exporter une classe vide au départ, etc.
Il existe des outils qui vous évitent de devoir développer vous-même ce genre de code redondant. On parle de Snippets. Il en existe plusieurs en fonction de votre 

IDE:
1. Visual Studio Code.
2. Atom.
3. Sublime Text.
Les snippets définissent des raccourcis qui vous permettent de mettre en place en quelques clics l'architecture de certains éléments. Par exemple, pour mettre en place l'architecture de base d’un composant, on pourra utiliser le raccourci ng-component. La snippet s'occupera alors de générer un composant générique, qui respecte les conventions de nommage que nous avons vues !

## En résumé

1. La documentation officielle d'Angular propose un guide qui répertorie toutes les bonnes pratiques de développement, avec une justification pour chaque recommandation.
2. Codelyzer est l'outil recommandé pour vérifier automatiquement si notre code respecte les recommandations de la documentation.
3. Il existe des snippets pour nous accélérer nos développements, en générant des bouts de code génériques qui respectent les recommandations d'Angular.

## Introduction
Lorsque nous avons développé l'application de ce cours, nous nous sommes contentés de copier-coller le fichier de configuration de TypeScript fournis par la documentation officielle. Mais que savons-nous exactement de ce fichier, et de son fonctionnement ? Pas grand chose, en fait.
Le but de ce chapitre est de faire la lumière sur le fichier de configuration tsconfig.json, que l'on retrouve dans toutes les applications développées avec TypeScript !
Le fichier de configuration de TypeScript
Lorsque l'on utilise TypeScript dans un projet, il faut ajouter le fichier de configuration tsconfig.json dans le dossier du projet, pour guider le compilateur dans la génération du code JavaScript.
Voici le fichier de base, tel qu'il est configuré pour faire fonctionner le projet que vous avez réalisé pendant ce cours:
```
{
 "compilerOptions": {
 "target": "es5",
 "module": "commonjs",
 "moduleResolution": "node",
 "sourceMap": true,
 "emitDecoratorMetadata": true,
 "experimentalDecorators": true,
 "removeComments": false,
 "lib": [ "es2015", "dom" ],
 "noImplicitAny": true,
 "suppressImplicitAnyIndexErrors": true
 }
}
```

Ce fichier contient seulement les éléments et les options qui sont essentiels pour une application Angular.
Nous allons d'abord voir les options existantes, et ensuite quels sont les éléments qui peuvent être ajoutés pour améliorer cette configuration initiale, dans les sessions suivantes.
Vous trouverez plus d'information sur le fichier tsconfig.json sur la page dediée dans la documentation officielle de TypeScript.

# La configuration existante
Voici point par point les éléments de notre configuration actuelle:

1. target: Cette option permet de spécifier la version d'ECMAScript souhaitée : es3, es5 ou es6. Il est recommandé d'utiliser la version es5 actuellement.
2. module: Permet de Spécifier le module de génération de code. Les valeurs possibles sont : 'none', 'commonjs', 'amd', 'system', 'umd', 'es6' ou 'es2015'. Choississez la manière dont vous souhaitez apporter la modularité dans votre application.
3. moduleResolution: S'occupe de la modularité de votre application. Mettez la valeur 'classic' si vous utilisez 'amd', 'es6' ou 'system', sinon laissez 'node'.
4. sourceMap: Souhaitez-vous générer des fichiers *.jsmap ou non ? Ces fichiers map servent débogueur de votre IDE pour faire le lien entre le code JavaScript exécuté et les fichiers sources originaux écrits en TypeScript, rendant ainsi le débogage de votre application plus facile.
5. emitDecoratorMetadata: Vous devez renseigner un booléen. Faut-il générer des méta-données pour les annotations présentes dans le code source (c'est-à-dire prendre en compte les annotations des fichiers sources ?) La réponse est oui, bien sûr !
6. experimentalDecorators: Activer le support expérimental pour les décorateurs ES7.
7. removeComments: Souhaitez-vous retirer les commentaires contenus dans les fichiers sources ? (excepté les en-têtes avec /*!, qui sont utilisés pour spécifier des copyright).
8. lib: Liste des fichiers de librairies à inclure dans la compilation.
9. noImplicitAny: Faut-il soulever des erreurs sur les variables dont le type any a été attribué implicitement par TypeScript. Choisir une valeur pour cette option peut être délicat, nous allons voir pourquoi dans la prochaine session.
10. suppressImplicitAnyIndexErrors: Sans rentrer dans les détails, permet d'ajouter un peu plus de souplesse à l'option noImplicitAny. On va traiter de ce point dans la prochaine session.

## L'option noImplicitAny

Il n'y a pas de vérité absolue à propos de la valeur à attribuer à l'élément noImplicitAny. Cependant, votre choix peut être impactant si vous travaillez sur des projets de tailles importantes.
Quand l'option noImplicitAny est définie à false (qui est la valeur par défaut), si le compilateur ne peut pas déduire le type d'une variable en fonction de la façon dont elle est utilisée, le compilateur ajoutera implicitement le type any à cette variable.
Lorsque TypeScript détermine tout seul le type d'un variable, on dit que le type est inféré par le compilateur.
Jusqu'à maintenant, on a laissé cette valeur à false pour faciliter l'apprentissage de TypeScript.
Cependant, quand cette valeur est définie à true, et que le compilateur ne peut pas inférer le type d'une variable, il va générer les fichiers JavaScript, mais il lèvera également une erreur !
Beaucoup de développeurs chevronnés préfèrent ce paramètre, plus strict, parce que cette vérification de type permet de lever plus d'erreurs involontaires lors de la compilation.
Si vous définissez l'option notImpicitAny à true, vous pourriez obtenir des erreurs implicites du compilateur. Ces erreurs particulières sont plus ennuyeuses qu'utiles. On peut supprimer ces erreurs en ajoutant l'option suivante:

``` suppressImplicitAnyIndexErrors': true ```

On peut définir le type d'une variable à any même quand l'option noImplicitAny est définie à true !

## Les configurations supplémentaires

Il existe certaines options que vous pouvez ajouter à la configuration de base du compilateur:

1. outDir (chaîne de caractère): Cette option permet de définir un nom de dossier dans lequel seront ajoutés les fichiers JavaScript générés par le compilateur. Nous avons utilisé cette option au début de ce cours, dans le chapitre "Hello, World !" avec Angular. On utilise généralement le nom de dossier "dist", qui signifie distribution.
2. pretty (booléen): Si définit à true, cette option permet d'ajouter des couleurs aux messages d'erreurs du compilateur dans la console. Cela ne coûte pas cher et c'est bien pratique !
3. charset (UTF-8): Permet d'encoder en UTF-8 les fichiers générés par le compilateur.
4. locale (fr, par exemple): La locale à utiliser pour afficher des messages d'erreurs.

Voici une liste exhaustive des configurations possibles pour tsconfig.json.

## Conclusion

Nous avons pu voir plus en profondeur comment configurer TypeScript dans un projet.
N'hésitez pas à vous référez à la documentation officielle si vous souhaitez en savoir plus. Cependant, avec ce que nous venons de voir, vous en savez bien assez pour commencer le développement de vos applications sereinement, plus d'excuses !

## En résumé

1. La configuration de TypeScript dans un projet repose sur le fichier tsconfig.json.

## Introduction

Ce chapitre a pour objectif de détailler les dépendances nécessaires au démarrage d'un projet Angular. Nous allons voir précisément quelles sont ces dépendances, et pourquoi elles sont indispensables.
Bien sûr, vous n'avez pas besoin de connaître parfaitement les dépendances d'un projet avant de commencer à développer. Cependant, c'est toujours un plus si vous maîtrisez un peu mieux votre environnement de développement.
Les dépendances d'un projet Angular
Les applications Angular (et Angular lui-même) dépendent de fonctionnalités fournies par des librairies. Ces librairies sont maintenues et installées avec le Node Package Manager: on parle de paquets.
Node.js et NPM sont essentiels aux développements d'applications Angular: installez-les sur votre machine avant de pouvoir commencer à développer.
Vérifiez que vous disposez de node 4.x.x ou plus, et npm 3.x.x ou plus, grâce aux commandes node -v et npm -v dans une fenêtre de terminal. Les versions plus anciennes causent des erreurs !

Il est recommandé de démarrer son projet Angular avec un ensemble de paquets, spécifié dans le fichier package.json:
```
"dependencies": {
  "@angular/animations": "^5.0.0",
  "@angular/common": "^5.0.0",
  "@angular/compiler": "^5.0.0",
  "@angular/core": "^5.0.0",
  "@angular/forms": "^5.0.0",
  "@angular/http": "^5.0.0",
  "@angular/platform-browser": "^5.0.0",
  "@angular/platform-browser-dynamic": "^5.0.0",
  "@angular/router": "^5.0.0",
  "angular-in-memory-web-api": "^0.5.2",
  "core-js": "^2.4.1",
  "rxjs": "^5.5.2",
  "systemjs": "0.19.40",
  "zone.js": "^0.8.14"
}, ...
```
Bien sûr, vous pouvez utiliser d'autres versions des paquets que celles indiqués ici, il s'agit juste des dernières versions disponibles au moment où j'écris ces lignes. Nous allons voir le rôle de chacun de ces paquets. Vous pourrez faire des substitutions plus tard, en fonction de vos goûts et de votre expérience.

## Les dépendances de l'application

Le fichier package.json inclut deux ensembles de paquets différents : dependencies et devDependencies.

• La section dependencies est essentielle pour l'exécution de l'application.
• Les devDependencies sont seulement nécessaires pour développer l'application.
On peut exclure les paquets devDependencies de l'installation grâce à la commande suivante : npm install --production.
Les paquets de fonctionnalités
La section dependencies du package.json contient plusieurs types de paquets : les paquets de fonctionnalités, des polyfills et des utilitaires en plus.

1. @angular/core: C'est la pièce maitresse du framework, nécessaire pour toutes les applications. Inclut toutes les annotations @Component, @Directive, l'injection de dépendances et les cycles de vie des composants.
2. @angular/common: Ce paquet contient les services couramment nécessaires, les pipes et les directives fournis par l'équipe de développement d'Angular.
3. @angular/compiler: Le compilateur de template d'Angular interprète les templates et les convertit en code pour rendre l'application fonctionnelle. En générale, on n'interagit pas directement avec le compilateur. A la place, on utilise le paquet platform-browser-dynamic ou platform-browser.
4. @angular/platform-browser: Ce paquet inclut la méthode bootstrapStatic pour démarrer l'application à destination de la production, pré-compilant tous les templates à l'avance, avant de les envoyer dans le navigateur.
5. @angular/plateform-browser-dynamic: Inclut la méthode bootstrap pour les applications qui compilent les templates côté client. Utiliser ce paquet pour démarrer l'application plutôt durant le développement.
6. @angular/common/http: Le client HttpClient d'Angular.
7. @angular/router: Le routeur, et d'autres utilitaires pour faire fonctionner la navigation dans votre application.
8. System.js: Un chargeur dynamique de modules compatible avec la spécification des modules ES2015.

Vos applications futures sont susceptibles d'avoir besoin de paquets supplémentaires, pour fournir des directives, des thèmes, faciliter l'accès aux données et autres utilitaires. Il faudra alors ajouter ces dépendances dans le fichier package.json.

## Les paquets de supports & Polyfill

Angular requiert certains paquets de supports et polyfills pour faire fonctionner une application. Vous devez lister ces éléments parmi les paquets de la section dependencies. Il y a trois paquets recommandés au démarrage d'un projet:

1. CoreJs: Un polyfill qui corrige le contexte global (window) avec les fonctionnalités essentielles d'ES6. Quand ES6 sera implémentée par les principaux navigateurs, cette dépendance deviendra inutile.
2. RxJs: Un paquet de support concernant la spécification des Observables. Voici pouvez choisir la version de RxJs que vous préférez (dans une plage de version compatible), sans avoir besoin d'attendre les mises à jour d'Angular.
3. ZoneJs: Un paquet de support pour la spécification des zones, qui fournissent un contexte d'exécution pour les opérations asynchrones. Comme pour RxJs, vous pouvez choisir la version de zone que vous préférez (dans une plage de version compatible également, bien sûr !).

## Les autres librairies

1. angular-in-memory-web-api: Une librairie qui simule un serveur web distant sans avoir besoin d'en installer un. C'est très pratique pour les démonstrations, les exemples, et les développements à un stade précoce.

## Les dépendances de développement
Les paquets listés dans la section devDependencies nous aident seulement à développer l'application. Nous n'avons pas besoin de les déployer en production. Voici les paquets les plus importantes en rapport avec ce cours:

1. concurrently: Un utilitaire pour pouvoir exécuter des commandes NPM sur différents systèmes d'opérations comme OS/X, Windows et Linux ;
2. lite-server: Un serveur de fichiers statiques léger, avec un excellent support pour les applications Angular qui utilisent le Router ;
3. typescript: Tout ce qui est nécessaire pour pouvoir utiliser TypeScript, incluant le compilateur tsc.

## Conclusion
Nous avons pu décortiquer toutes les dépendances initiales d'un projet Angular. Même si ce n'est pas indispensable de connaître le fonctionnement de chaque dépendance, cela nous permet de savoir un peu mieux où l'on met les pieds, et on se sent toujours plus à l'aise quand on développe avec des outils que l'on connaît !

## En résumé

1. Il est nécessaire d'installer Node.js et NPM sur sa machine pour pouvoir développer des applications Angular.
2. Les librairies chargées par NPM sont appelées des paquets.
3. Il y a deux types de paquets à déclarer : les dépendances et les dépendances de développement.
4. Les dépendances sont les paquets nécessaires pour que l'application puisse fonctionner.
5. Les dépendances de développement sont des paquets permettant aux développeurs de développer l'application.











