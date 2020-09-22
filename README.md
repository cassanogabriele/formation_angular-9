
## Fichier app.component.ts
// Composant parent du point d'entre de l'application 

// Imports Angular

// Importation des éléments dont on a besoin : import "nom_de_l'élément" from "nom_packet_source"
import { Component } from '@angular/core';
// Import de l'interface depuis le coeur d'Angular qu'on va utiliser
import { OnInit } from '@angular/core';

import { Pokemon } from './pokemon';
// Import de la constance "POKEMON"
import { POKEMONS } from './mock-pokemons';
 
// Permet de définir le composant 
@Component({
	selector: 'pokemon-app',
	// template: `<h1>Liste de pokémon</h1>`,
	/*template : 'Ceci est un template très très '
	+ ' très très '
	+ 'long'*/
	// Chemin vers le template, dans le même dossier que le composant
	// On doit mentionner le chemin relatif par rapport au dossier source
	templateUrl : `./app/app.component.html`,
})

// Code de la classe du composant : contient la logique du composant, export permet de rendre le composant accessible pour d'autres fichiers  
// "Component" : convention
export class AppComponent implements OnInit  { 
	// Interpolation : composant se charge d'afficher "Hello Angular"
    // name = 'Angular'; 
	
	// On doit ajouter une propriété "pokémon" qui contiendra la liste des pokémons à afficher dans le template (objet de type Pokemon)
	private pokemons: Pokemon[];
	// Valeur qui va être récupéré automatiquement par Angular et qui sera injectée dans le template pour qu'elle affiche dans le navigateur le titre
	// Angular met aussi à jour l'affichage dans le template si la propriété du composante est modifiée sans avoir besoin de rien faire
	private title: string = "Pokémons";
	// private value : string = '';
	// values = '';
	age = 20;
		
	// On veut initialiser la liste de pokemon avec quelques éléments de base au chargement du composant
	// On veut intéragir sur le cycle de vie d'un composant, en particulier sur l'étape d'initialisation du composant
	ngOnInit() {
		// On est capable d'ajouter une étape d'initialisation au composant et on utilisera la méthode pour ajouter des données à la propriété "pokémon"
		
		// On ajoute un certain nombre de données à la propriété "POKEMON"
		this.pokemons = POKEMONS;
	}

	// Méthode qui est enclenchée au clic sur le bouton
	/*onClick(){
		console.log("Clic !");
	}*/

	// Affecter une nouvelle valeur à la propriété "value"
	/*onKey(event: keyboardEvent){
		// La méthode traite l'événement soulevé par l'utilisateur en mettant à jour la propriété "value" du composant.
		// Ces modifications sont ensuite immédiatement récupércutée directement dans le template.
		// La structure de l'objet "event" est déterminée à l'avance quel que soit l'événement qu'on va soulever, cela est du au fait
		// que cet objet représente un événement standard du DOM qui contient des propriétés et des méthodes communes à tous les éléments.
		// "event.target" renvoie un objet de type "html input element", un champ texte qui possède une propriété "value" qui contient 
		// les données entrées par l'utilisateur, on peut donc bien accéder au données entrées par l'utilisateur, depuis le composant.
		this.value = 'Bonjour ' + (<HTMLInputElement>event.target.value);
	}*/

	/*/onKey(value: string){		
		this.value = 'Bonjour ' + value;
    }*/

	// On ajoute une méthode pour gérer les interactions de l'utilisateur (si un utilisateur clique sur un pokémon de la liste, on va effectuer une action comme 
	// une redirection ou un affichage). La capture de l'interaction de l'utilisateur se fait côté template.

	// Méthode qui sera appelée lors de cet événement, elle prend en paramètre le pokémon sélectionné, on peut le typer 
	selectPokemon(pokemon: Pokemon){
		alert("Vous avez cliqué sur : " + pokemon.name);
	}	
}

## Fichier app.component.html (détail)
<h1 class='center'>Pokémons</h1>
<div class='container'>
<div class="row">
 <!-- On crée un nouveau bloc pour chacun des pokemon -->
<div *ngFor='let pokemon of pokemons' class="col s6 m4">
    <!-- Définir un bloc avec une image à gauche et un texte à droite -->
   <!-- On détecte le clic sur le bloc avec la fonction "selectPokemon" en passant en paramèter directement l'objet "pokemon" sur lequel l'utilisateur à cliqué. -->
    <div class="card horizontal" (click)="selectPokemon(pokemon)" pkmnBorderCard>
    <div class="card-image">
      <!-- Liaison de propriété : on met des [] pour qu'Angular puisse intepréter l'expression passée en paramètre.  -->
      <img [src]="pokemon.picture">
    </div>
    <div class="card-stacked">
      <div class="card-content">
        <p>{{ pokemon.name }}</p>
        <!-- Affichage de la date à l'utilisateur via l'interpolation.
        On ajoute un pipe avec l'opérateur "|" et le nom du pipe.
        -->
        <p><small>{{ pokemon.created | date:"dd/MM/yyyy" }}</small></p>
       <!-- -Liste des types Pokémon avec la bonne couleur correspondante -->
       <span *ngFor="let type of pokemon.types" class="{{ type | pokemonTypeColor }}">{{ type }}</span>
      </div>
    </div>
  </div>
</div>
</div>
</div>


<!--<input #box (keyup.enter)="values=box.value" (blur)="values=box.value">
<p>{{ values }}</p>-->

<!--<ul>
    <li>Bulbizarre</li>
    <li>Salamèche</li>
    <li>Carapuce</li>
    <li>Carapuce</li>
</ul>-->

<!-- Ecouter un clic sur un élément -->
<!-- <button (click)="onClick()">Cliquer ici !</button>
<!-- A chaque fois que l'utilisateur déclenche l'événement keyup (il tape du texte dans le champ "input" et qu'il relâche une touche),
la méthode "onKey" est appelée avec en paramètre un objet réprésentant l'objet soulevé.
--->

<!-- <input (keyup)="onKey($event)"> 
On a déclaré une variable box dans le template qui est une référence à l'élément "input" sur laquelle elle est déclarée.
On peut ensuite récupéré la valeur entrée par l'utilisateur grâce à la propriété "value" et ensuite l'afficher grâce à l'interpolation.
-->
<!-- <input #box {keyup}="0"> -->

<!-- <p>{{ value }}</p> -->
<!--input #box (keyup)="onKey(box.value)">-->


<!-- Au lieu d'appeler la propriété value du composant, on va directement appeler la variable locale du template.  
Interoplation : sert à aussi à afficher des variables référencées dans le template qui sont également référencés dans 
le template sont accessibles pour tous les éléments fils et frère de l'élément sur lequel elles ont été déclarées.
Le "keyup=0" est important car Angular prend en compte la liaison de données entre le composant et le template seulement si on 
effectue une action en réponse à des événements comme des frappes sur le clavier. Le 0 est la plus courte déclaration qu'on peut faire
pour signifier qu'on veut rien exécuter mais simplement activer la liaison de données entre la variable locale et la valeur interpolée (box.value). 
-->
<!-- Valeur entrée par l'utilisateur -->
<!-- <p>{{ box.value }}</p> -->
<!-- Si on veut afficher la valeur après la modification de la méthode "keyup" -->
<!-- <p>{{ value }}</p> -->

## Fichier "package.json" 

## Permet de générer une archive pour l'application
"build": "tsc -p src/"

## Permet de démarrer un miniserveur avec lite
"serve": "lite-server -c=bs-config.json"

## Permet de démarrer l'application 
"start": "concurrently \"npm run build:watch\" \"npm run serve\""

## Dépendances dont on aura plus besoin quand l'application sera terminée
"devDependencies"
## Ne nous servira plus quand l'application sera terminée car le navigateur ne pourra pas intérprété, seul le javascript, résultat de la compilation sera interprété
"typescript": "~3.8.3"
## Ne nous servira plus quand l'application sera terminée car le navigateur ne pourra pas intérprété, seul le javascript, résultat de la compilation sera interprété
"typescript": "~3.8.3"

## src/systemjs.config

## map : objet qui permet de déclarer de nouveau éléments 

## dossier app : code de l'application 

## mappgin des libraires : angular bundles, permet d'utiliser un alias pour l'importation dans l'application

## fichier de configuration du compilateur de typescript pour paramétrer des choses pour la compilation : src/ts.config.json
Fichier de configuration de typescript, on peut définir un certains nombre d'éléments, détails de la configuration qui sont dans la documentation officielle

## fichier de configuration qu'on ne touchera quasi jamais : bs-config
concerne le mini-serveur de développement utilisé, il permet de déclarer le dossier de base qui est "source" et de déclarer les "node_modules"

## npm install : dépendances node_modules

## best pratice : placer tous les fichiers dans un dossier app qui est dans un dossier "src"

## Un composant doit au moins importer la notation component

## Le "@Component" doit au moins comprendre 2 éléments obligatoires : "selector" (nom du composant pour l'identifier par la suite), "template" (permet de définir le code html du composant, on peut le template html dans un fichier à part avec l'instruction "template_url")

## Regrouper tous les composants par fonctionnalité, Angular le permet grâce aux modules, tous les composants seront regroupés au sein de modules

## Au minimum l'application doit contenir un module (module racine), ensuite au fur et à mesure que l'application avancera, on créera de nouveaux modules pour d'autres fonctionnalités

## compile tous les fichiers du projet et le lance dans un navigateur (vient du fichier "package.json")
npm start

## Un composant est une classe qui contrôle une portion de l'écran sur l'interface utilisateur, cette portion de l'écran contrôlée par le composant est une vue. On définit la logique du composant dans sa classe, ce qu'il faut pour faire fonctionner la vue. La classe du composant intéragit avec la vue à travers des propriétés et des méthodes 

## Un composant = une classe + une vue

## La vue est définie dans le template du composant

## L'interface OnIti fournit la méthode ngOnInit et permet de définir un comportement lorsque le composant est initialisé -> initialise le composant
ngOnInit(): void { }

## Il est conseillé de garde toute la logique de l'application en dehors du constructeur, surtout quand on commence à récupérer des données d'un serveur distant

## Le corps du constructeur peut éventuellement être utilisé pour des initialisations simples et dans ce cas là, il est recommandé de passer par ngOnInit()

## Les templates sont les vues des composants et contiennent le code de l'interface utilisateur

## Parfois les templates sont trop longs pour écrit dans le même fichier que le composant, même en utilisant les "backticks", il est préférable d'écrire le template dans un fichier à part. Angular propose l'option "templateUrl" : au lieu d'écrire le template en dur dans le composant, on peut mettre un chemin relatif vers le fichier du template.

## La manière la plus simple d'afficher la propriété d'un composant dans son template est d'utiliser le mécanisme d'interpolation. Avec l'interpolation, on peut afficher la valeur d'une propriété dans la vue d'un template entre 2 {}. Le fait que la propriété interpolée est mis à jour dans le template en cas de modification s'appelle le binding unidirectionnel, l'interpolation s'occupe de cela, en plus de l'affichage de la valeur de la propriété

## Quand il y a une interaction avec l'utilisateur, on veut en être informé au niveau du composant, toutes ces actions lèvent des actions dans le DOM (représentation structurée de la page HTML ou chaque balise représente un noeud) avec lequel on veut interagir. On peut lier n'importe quel élément du DOM à une méthode du composant en utilisant la syntaxe de liaison d'événement d'Angular.

## Pour écouter un événement, on entourre le nom de l'élément du DOM par des () et on renseigne une action à réaliser qui correspond à une méthode du composant.

## Il y a une autre manière de récupérer les données entrées par l'utilisateur sans la variable event : c'est une fonctionnalité d'Angular qui permet de déclarer des variables localas dans le template, elles garantissent un accès sur l'élément du DOM directement depuis le template. On déclare une variable locale avec l'opérateur '#'.

## Angular permet de filtrer les événements du clavier à travers une syntaxe spécifique, on peut écouter uniquement la touche entrée en utilisant le pseudo-évenement "keyup.enter".

## Les directives 
Une directive est une classe Angular qui ressemble beaucoup à un composant sauf qu'elle n'a pas de template. La classe Component hérite de directive, au lieu d'anoter la classe de directive avec "@component", on utilisera "@directive". Une directive permet d'intéragir avec des éléments HTML d'une page en leur attachant un comportement spécifique, on peut avoir plusieurs directives appliquées à un même élément. Une directive possède un "selector" css qui indique au framework ou l'activer dans le template. Angular trouve une directive dans un template HTML, il instancie de la classe correspondante et donne à cet instance le contrôle sur la portion du DOM qui lui revient.

## Les types de directives

## Les composants (app.component.ts)

## Les directives d'attributs 
Elles peuvent modifier le comportement des éléments HTML, des attributs, des propriétés et des composants. Elles sont représentées habituellement par des attributs au sein des balises HTML. Un directive d'attribut requiert au moins une classe annotée avec "@directive".

## Les directives structurelles 
Elles sont responsables de mettre en forme d'une certaine manière les élements HTML de la page en ajoutant, en retirant ou en manipulant des éléments et leur fils. Les directives ng-if et ng-for sont des directives structurelles.

## Nom des directives 
Il est recommandé de préfixer les noms des directives pour éviter le risque de collision avec des librairies tierces ou avec des attributs HTML standarg. Il ne faut pas utiliser "ng" comme préfixe pour les directives, ce préfixe est réservé par Angular et il faut utiliser la syntaxe camelcase pour nommer nos directives. 

## L'annotation @HostListener 
Elle permet de lier une méthode de la directive à un événement donné.

## L'alias
Il y a deux manières de déclarer une propriété d'entrée : avec ou sans alias. 
Sans alias, on est obligé d'utiliser le nom de la directive pour nommer la propriété qui n'est pas un nom adapté (dans le cas de l'exercice) pour la couleur des bordures. Grâce à l'alias, on peut nommer la propriété de la directive et utiliser ce nom ailleurs dans la directive. Il faut spécifier le nom de la directive dans l'argument @Input.

## Les formulaires
On la possiibilté d'utiliser deux modules différents : formsModule et ReactiveFormsModule qui répondent aux même besoins mais avec une approche différente. Ces deux modules viennent de la même librairie "#angular/forms".

## FormsModule 
Développe une partie importante du formulaire dans le template qui est le Template-driven-forms. Il est plus adapté pour les petits formulaires et pour se faire la main en tant que débutant.

## ReactiveFormsModule
Il est plus centré sur le développement du formulaire côté composant. 

## NgForm 
A partir du moment ou FormsModule à été importé, la directive ngForm est disponible sur toutes les balises "form" disponibles dans le module ou on ou a importé le FormsModule, on a pas besoin d'ajouter de sélecteur supplémentaire dans le template. Pour chaque formulaire ou elle est appliquée, la directive ngForm va créer une instance de l'objet "FormGroup" au niveau global du formulaire. Une référence à cette directive permet de savoir si le formulaire que remplit l'utilisateur remplit est valide ou non au fur et à mesure que l'utilisateur complète le formulaire. On peut être notifié lorsque l'utilisateur enlenchera la soumission du formulaire.

## ngModel 
Elle doit s'appliquer sur chacun des champs du formulaire. Cette directive crée une instance d'un objet "FormControl" pour chaque champ du formulaire comme "input" ou "select". Chaque instance de "FormControl" constituera une brique élémentaire qui encapsulera l'état donné d'un champ, il a pour rôle de traquer la valeur du champ, les interactions avec l'utilisateur, la validité des données saisies et de garder la vue synchronisée avec les données. Chaque "FormControl" doit être définit avec un nom, il faut ajouter l'attribut "name" à la balise HTML associée. Lorsque la directive est utilisée au sein d'une balise "form", la directive s'occupe de l'enregistre auprès du formulaire comme un élément fils du formulaire. En combinant cette directive avec la directive ngForm, on peut savoir en temps réel si le formulaire est valide ou non. Cette directive s'occupe de mettre en place une liaison bi-directionnel pour chacun des champs du formulaire dont on aura souvent besoin pour gérer les interactions de l'utilisateur, côté template et traiter les données saisies, côté composant. La directive s'occupe également d'ajouter ou de retirer des classes spécifiques sur chaque champ pour savoir si l'utilisateur a cliqué ou non sur un champ, si la valeur du champ a changé ou si il est devenu invalide. En fonction des informations, on pourra changer l'apparence d'un champ et faire apparaître un message d'erreur ou de confirmation à l'utilisateur. 

## ngModelGroup 
On peut aussi l'utiliser pour créer des sous-groupes de champs à l'intérieur du formulaire.

## Le pipe 
Grâce à l'interpolation, on peut afficher des données dans les templates mais parfois les données que l'on récupère ne peuvent pas être affichées directement à l'utilisateur. Le cas des dates est l'exemplaire le plus courant, on peut recevoir un format brut qui ne correspond pas à ce qu'on veut afficher à l'utilisateur. On aura besoin de formater l'affichage afin d'afficher quelque chose de plus lisible. On a souvent besoin d'effectuer les mêmes transformations dans plusieurs templates différents à travers le projet. Angular dispose des pipes pour effectuer plus simplement ces transformations dans le template.

## Utiliser un pipe 

## Les pipes disponibles par défaut 
Il y a un certain nombre de pipe, comme "date" fournis par Angular, immédiatemment disponibles dans tous les templates (voir la documentation). Les pipes sont pratiques pour formater des données trop brutes au sein des templates : plutôt que de définir les mêmes transformations à travers plusieurs composants, on peut développer des pipes personnalisés pour centraliser la définition de ces transformations. Il ne faut pas hésiter à utiliser les pipes dès qu'on juge que c'est nécessaire.np

## Combiner les pipes
Il est possible d'utiliser plusieurs pipes différents pour une même propriété et de les combiner pour obtenir l'affichage souhaité (exemple : afficher les dates en majuscules).

## Paramètrer les pipes 
Les pipes peuvent faire l'objet d'une utilisation plus poussée : il est possible de passer des paramètres au "pipes" afin de mieux définir l'affichage souhaité. Pour connaître tous les paramètres qu'on peut passer au "pipes" présents par défaut dans une application Angular : https://angular.io/guide/pipes.

## Les routes 
Le système de navigation fournit par Angular simule parfaitement la navigation auprès du navigateur. Lorsqu'on naviguera dans l'application, on pourra revenir en arrière via le bouton du navigateur, ça fonctionnera. On peut également entrer une url dans la navigateur pour rejoindre une page de l'application et l'historique du navigateur sera automatiquement mis à jour par Angular, il simule la navigation auprès du navigateur même si l'application ne fait qu'afficher et masque des éléments à l'utilisateur. Les routes dans une application doivent être regroupées par grande fonctionnalité au sein de modules. Toutes les routes concernant les pokémons doivent être centralisées au même endroit, dans le même module et toutes les routes concernant d'autres aspect de l'application, comme l'authentification, l'inscription doivent être gérées dans un autre module.

## Fonctionnement de la navigation
Pour mettre en place un système de navigation, on aura besoin d'au moins 2 composants.

Le composants de la liste des pokemons, accessible à l'url : /pokemons.
Quand on clique sur un pokémon, on est redirigé vers une page "pokemon/id du pokémon", qui affiche des informations supplémentaires sur le pokémon. Un bouton retour permet de retourner à la page qui liste les pokémons.

On crée 2 composants dans le dossier "app" du projet : 

- un composant "liste pokémon" qui affichera la liste de tous les pokémons de l'application accessible à l'url "/pokemons"
- un deuxième composant "detail-pokemon.component" qui sera chargé d'afficher une page d'informations spécifique pour un pokemon qui sera chargé à l'url "pokemon/id du pokemon".

## <router-outlet></router-outlet>
Quand on naviguera dans l'application, le template des composants parcourus sera injecté immédiatemment au sein de la balise "router-outer".

## Le routeur
Par défaut, le routeur d'une application n'a pas de route jusqu'à ce qu'on les configure.

2 façons de faire : 

1. On peut définir les routes sous forme d'une constante de type "tableau" et les déclarer directement dans le fichier du module racine "app.module.ts".

2. Appliquer un découpage plus systématique et déclarer les routes dans un module dédié (comme fais dans la formation). Cette méthode est recommandée car elle permet de mieux découper la structure de l'application et on peut configurer plus facilement des modules de routes pour chaque 
fonctionnalité ou partie de l'application

Il ne faut jamais mélanger les deux manières de faire dans le même projet, il faut choisir dès le départ la manière qui nous convient le mieux.

## Module 

## Ajouter un nouveau module 
Les application Angular sont modulaires et elles possèdent leur propre système de module. Chaque application possède au moins un module : le module racine, "app.module", il peut suffir pour de petites applications mais la plupart des projets ont besoin de plusieurs modules, des modules de fonctionnalité (pour chaque fonctionnalité, on a va ajouter un nouveau module), qui sont donc qu'un ensemble de classes et d'éléments spécifiques de l'application. Quel que soit la nature du module, un modul est toujours une classe avec le décorateur "@NgModule" qui prend en paramètre un objet qui décrivent le module. "déclarations" sont les classes de vues, Angular à 3 types de classes de vues : Composant, Directives et Pipes, il faut renseigner toutes les classes de vues dans le tableau de déclarations. Il y a aussi une option "Exports" qui est un sous-ensemble de classes de vues à exporter. "Imports" concerne les classes nécessaires au fonctionnement du module dont on a besoin dans le module. "Providers" est une propriété qui concerne les services et l'injection de dépendandces et permet de fournir un service au module. "Boostrap" est une propriété qui ne concerne que le module racine, il faut y renseigner le composant racine, qui sera affiché au lancement de l'application. JavaScript à son propre système de modules qui est complètement différent et sans rapport avec le système de module d'Angular. En JavaScript, chaque fichier est un module et tous les objets définis dans ce fichier appartiennent au module. Le module JavaScript déclarer certains objets comme "public" en les déclarant avec le mot clé "export", d'autres modules javascript utilisent le mot clé "import" pour accéder à ces objets, c'est ce mécanisme utilisé dans Angular pour les imports et exports. Les systèmes de modules de JavaScript et de Angular sont différents mais complémentaires et on utilise bien les deux pour écrire une application.

## BrowserModule
Il inclut le CommonModule, ce qui fournit un certain nombre d'éléments dans les templates des composants comme les directives "ng-if" et "ng-for". La spécificité du BrowserModule qu'on utilise dans le module racine est qu'il permet de démarrer l'application dans le navigateur, on a pas besoin de faire cela dans tous les modules, le CommonModul est suffisant, c'est le module par défaut qu'il faut importer pour tous les sous-modules, qui ne sont pas le module racine de l'application.

## Le tableau Declarations 
On déclare les composants, les directives et les pipes propres au module.

## Le tableau providers 
C'est dans ce tableau qu'on peut déclarer des services propres au module.

## Dossier app/pokemons
C'est dans ce dossier qu'on va placer tous les éléments relatifs au module "pokemon module" : les tempaltes, les composants, les routes, les directives, les pipes, etc.  

## Les modules 
Ils sont destinés à regrouper des fonctionnalités indépendantes les unes des autres, le plus possible et donc chaque module doit posséder les routes qui lui sont propres en interne.

## Les routes 
Il ne faut surtout pas utiliser la méthode "forRoute" dans des fichiers de définition des routes des sous modules, sous peine de lever une erreur. Elle est réservée pour la déclaration des routes au niveau du module racine de l'application et ensuite dans tous les sous-modules de déclaration de routes, il faut utiliser la méthode "forChild". Le routeur se chargera ensuite de combiner et assembler toutes les routes de l'application. Cela permet de définir les routes de l'application. Cela permet de définir les routes des sous modules sans avoir à modifier les routes principales de la configuration.

## Structure de l'application 
L'architecture de l'appication est déjà en place, elle comprend 2 modules nécessaires pour développer l'application finale : le module racine "app.module" et un sous-module pour gérer les pokémons "pokemon.module.ts". L'application finale va simplement pemetttre de gérer des pokémons, l'utilisateur pourra donc se connecter à son espace privé et pourra ensuite modifier des pokémons à sa disposition. Cet espace privé de l'utilisateur, on le gère dans le module "pokemon.module" dans lequel on pourra ajouter les éléments nécessaires au développement au fur et à mesure. On ajoutera un module "login.component" à la racine pour permettre à l'utilisateur de se connecter, cette fonctionnalité n'est pas relative directement à la gestion de pokémons, c'est pour cela qu'on la met au niveau de la racine. L'architecture de l'application est déjà en place.

## Organisation 
Il faut regrouper les fonctionnalités en modules, cela permet de créer des applications plus importantes sans s'emmêler les pinceaux au niveau du code. On va ensuite refactoriser le code présent dans plusieurs composants différents.

## Récupérer une instance de service dans le composant 

## A NE PAS FAIRE 
constructor(
  ## déclarer une variable et instancier une nouvelle instance de PokemonService
  let pokemonsService = new PokemonService; 
}

Il y a 3 problèmes : 

- le composant devra savoir comment créer le "PokemonService", si on modifie le constructeur du service par la suite, on devra retrouver chaque composant ou on a utilisé ce service et c'est pas une bonne solution
- on crée une nouvelle instance du service à chaque fois qu'on va utiliser le mot clé "new". Si le service doit mettre en cache des pokemons et les partager avec tous les composants, on ne pourra pas le faire avec ce système car on aura besoin d'une instance unique à travers toute l'application.
- lorsqu'on développe un service, le consommateur du service ne doit pas se demander comment fonctionne le service de l'intérieur, il doit s'agir d'une boîte noire prête à l'emploi et dont le fonctionnement interne n'intéresse pas les composants consommateurs

## Comment créer un service dans un composant ? 
Angular propose d'injecter les services dans les composants plutôt que de les instancier nous même. L'injection d'un service dans un composant est très simple, on peut le faire en deux lignes : 

- ajouter un constructeur qui définit une propriété privée 
- ajouter un fournisseur (provider) pour le service grâce aux annotations

Comme on utilise l'injection de dépendance, Angular garantit que l'instance du service est unique à travers toutes l'application. Si on injecte le même service dans un autre composant, ce sera la même instance du service. Comme l'instance est unique, cela permet d'utiliser les services comme stockage provisoire des données.

Souvent, on aura besoin d'injecter un service dans un service, le fonctionnement est le même que pour les composants : il faut utiliser également le constructeur pour injecter le service, on parle du "constructor injection pattern". 
