
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

## Fournir un service 
Angular sait fournir l'instance de "pokemonService" lorsqu'on crée un nouveau "list.pokemon.component", on aura une erreur si on lance l'application car il faut également fournir un provider. Lorsqu'on fournit un service dans un composant, ses composants fils y ont également accès.

## Injection des dépendances 
Angular dispose de son propre framework d'injection et on ne peut pas vraiment développer une application sans cet outil. Il est nécessaire d'utiliser son injection de dépendances plutôt que des constructeur pour gérer les dépendances. L'injection de dépendance est un modèle de développement (design pattern) dans lequel chaque classe reçoit ses dépendances d'une source externe plutôt qu'en les créant elle même. Le système d'injection de dépendances d'Angular possède un "injecteur", on l'utilise pour gérer les dépendances au lieu de les gérer nous même. Par contre, on doit enregistrer des fournisseurs pour rendre disponible le service là ou on en a besoin : au niveau d'un module, d'un composant ou de toute l'application.

## Fournir un service à toute l'application 
Ca arrive parfois qu'on ait besoin de le faire, pour cela, on doit placer le fichier du service au niveau du dossier "app" et ensuite on doit fournir le service au niveau du module racine de l'application. Il faut l'importer au début du fichier et ensuite déclarer un fournisseur directement au niveau du module racine et puis renseigner le nom du service, il sera disponible dans toute l'application et on aura plus à l'ajouter manuellement pour l'utiliser dans les composants.

## Fournir un service à un module
Dans le cas ou le service ne doit être disponible que dans un module, il est inutile de leur fournir au niveau de toute l'application. On supprime l'annotation "providers" dans "list.pokemon" et "details.pokemon". Il faut ensuite se rendre dans le module pokémon : "pokemon.module.ts" et déclarer le pokémon service dans le tableau "providers". On ne sera plus obligé de fournir le service pour chaque composant du module qui en aurait besoin, il sera disponible directement. Il ne reste plus qu'à l'injecter via le constructeur du composant. Il est recommandé d'être toujours le plus précis possible dans la stratégie de "providers", ne jamais fournir tous les services à travers l'application si cela n'est pas nécessaire et les injecter seulement quand on en a besoin.

## Fournir un service à un seul composant
Si on doit fournir un service à un seul endroit dans un composant, on peut utiliser l'anotation "@component" avec la propriété "providers".

## Les formulaires 
Ils sont omniprésents dans l'application, la gestion des formulaires est complexe entre le traitement des données utilisateurs, la validation, l'affichage de message d'erreur ou de succès qui demande beaucoup de travail pour offrir une expérience complète et agréable pour l'utilisateur. Angular peut aider à créer des formulaires.

## Formulaire d'édition 
Lorsque l'utilisateur cliquera sur un pokémon, il pourra l'éditer et lorsqu'il cliquera dessus, il y a un formulaire permettant de modifier toutes les informations d'un pokémon.

## Formulaire pour l'édition d'un pokemon 
On ne modifie pas l'identifiant, ni la date de création d'un pokémon car ces données ne sont pas appelées à être modifiée, il reste le point de vie, les dégâts, le nom et ses différents types, formulaire à 4 champs. Le formulaire sera un composant à part entière chargé de gérer les données saisies par l'utilisateur et qui permettra d'éditer un pokémon. On va découper le template et le composant dans deux fichiers séparés, la classe du composant dans le fichier "pokémon-form.compoennt.ts" et le template du composant qui aura le même nom et qui sera un fichier HTML.

## Les composants avec une propriété d'entrée
Ils sont souvent les fils d'autres composants parce qu'ils dépendent d'eux pour récupérer la valeur d'entrée. Le composant de formulaire sera le fils d'un autre composant "edit-pokemon.component" qui sera chargé de lui transmettre le pokémon à modifier.

## Les champs du formulaire
(ngSubmit) : permet de lier l'événement de validation du formulaire à la méthode "onSubmit()" du composant chargé de gérer la soumission du formulaire.

On utilise la directive ngForm pour déclarer une variable de template "pokemonForm" qui permettra d'avoir accès à l'état de validité du formulaire ailleurs dans le template.

La directive ng-if assure qu'un pokémon a bien été transmis au composant du formulaire, dans le cas contraire on affiche un message d'erreur à la place du formulaire.

Chaque champ du formulaire est réprésenté par un bloc de code. L'utilisation de la directive ngModel permet la liaison bi-directionnelle entre le composant et le template : [()] est la combinaison de la liaison des propriétés (property binding) pour pousser une valeur du composant vers le template et de la liaison d'événement du template vers le composant (event binding).

La variable de déclaration du template "name", en lui associant la directive "ngModel", permet de déclarer le champ sur lequel elle est rattachée comme étant un objet de type "form-control". Le champ est ainsi rattaché au formulaire global et on peut obtenir des informations dessus : est-il valide ? a-t-il déjà été modifié par l'utilisateur ou non ?

Le champ qui gère les types de pokémon est plus complexe : 

- On utilise la directive "ng-for" pour créer une liste de cases à cocher avec un type de pokémon associé à chaque checkbox.
- On utilise le nom du type du pokémon pour lier la balise input et label grâce à l'interpolation et à la liaison l'attribut "for". 
- On définit le nom du type comme valeur du champ 
- On coche automatiquement la case si le pokémon possède déjà le type associé à cette case
- A chaque fois que l'utilisateur coche ou décoche une case, on déclenche un appel à la méthode "selectType" avec le type qui a été ajouté ou retiré pour réajuster le modèle côté composant 
- On applique le pipe "pokemonTypeColor" pour afficher un petit label de couleur pour afficher le nom du type à côté de chaque case à cocher.

## Ajouter le bouton de validation du formulaire
On utilise la liaison de propriété "disabled" pour désactiver le bouton de validation si le formulaire est invalide, cela oblige l'utilisateur à avoir correctement remplit tous les champs auparavant.

## Ajouter des règles de validation 
Le champ nom sera obligatoire et devra contenir une chaîne de caractères de 1 à 25 lettres uniquement. La quantité de point de vie d'un pokémon sera forcément un nombre compris entre 0 et 999, la quantité de dégats sera un nombre compris entre 0 99 seulement. Pour les types du pokémon, l'utilisateur devra sélectionner obligatoirement entre 1 à 3 types pour chaque pokémon. Les 4 champs du formulaire seront obligatoires. Les 4 premières règles peuvent être implémenter grâce aux nouvelles règles de l'HTML5, required, pour rendre un champ obligatoire et pattern qui permet de définir une expression régulière pour valider un champ (https://www.w3schools.com/tags/att_input_pattern.asp). 

## Prévenir l'utilisateur en cas d'erreur
On doit prévenir l'utilisateur sur ce qui ne fonctionne pas, on va utiliser les classes ajoutées automatiquement par la directive "ng-model" pour utiliser ces classes avec le css en ajoutant une bordure verte ou rouge en fonction de la validité des champs du formulaire, cela permet à l'utilisateur d'avoir un retour visuel sur l'état de validité d'un champ. Ensuite, on peut utilser ces classes avec les variables de template et la directive "ng-if" pour afficher un message en cas d'erreur sur un champ. On doit ajouter une feuille de style qui s'appliquera uniquement sur le composant du formulaire, qui est le comportement par défaut d'un composant Angular. 

Pour respecter le principe d'une tâche-1 fichier, on crée une feuille de style a part ("pokemon-form.component.css) : on affiche une bordure verte à gauche si un champ requis est valide, sinon on affiche un bordure rouge pour les éléments invalides qui ne sont pas des éléments de type "form" : input, select, etc. Les classes du fichier css ont été autoamatiquement ajoutés par la directive "ng-model". On doit lier le composant de formulaire à la nouvelle feuille de style, on peut passer plusieurs feuilles de styles à un composant mais pour un seul template. On peut également utiliser l'attribut "styles" et au lieu de passer un chemin relatif, on peut passer directement des propriétés css mais si le code est trop long et qu'on veut une application bien organisée, ce n'est pas conseillé et les feuilles de styles sont souvent communes à plusieurs composants, c'est préférable de les centraliser dans des feuilles de style à part. 

## Intégration du formulaire
Avant de pouvoir utiliser un formulaire, il faut l'intégrer dans l'application existante. 
La syntaxe entre [] indique une liaison de propriétés sur la propriété d'entrée du composant.

## Développer le composant du formulaire directement dans EditPokemonComponent 
Il est possible de le faire mais si on veut réutiliser ce formulaire pour ajouter un pokémon, dans ce cas le formulaire serait à part et pourrait être intégré à deux composants différents dans l'application. Il faut toujours respecter le principe d'une tâche = 1 fichier, cela s'applique aussi pour les formulaires. Le composant "edit-pokemon" est complet et utilisable partout pour permettre à l'utilisateur d'éditer ses pokémons.  

## Conclusion sur les formulaires 
Même si Angular simplifie la tâche, il faut quand même un peu  de travail. A chaque fois qu'on recharge les données dans le navigateur, les données concernant les pokémons sont réinitialisés et les changements ne sont pas pris en compte. Il faut les persister sur un serveur distant afin de donner une mémoire à l'application.

## Comment communiquer avec un serveur distant ?
Il y a plusieurs manières de faire : on peut faire des appels sur le réseaux avec des promesses ou avec les "observable" et la programmation reactive. 

## Les promesses 
Elles sont natives en JavaScript depuis ES6, ce n'est plus un objet interne à Angular, on peut les utiliser sans avoir besoin de nouvelles importations. Elles sont là pour essayer de simplifier la programmation asynchrone qui désigne un mode de fonctionnement dans lequel les opérations sont non bloquantes : l'utilisateur peut continuer à utiliser l'application web en naviguant et en remplissant des formulaires sans que le site soit bloqué dès qu'on fait un appel au serveur. On peut aussi utiliser des fonctions de callback pour gérer les appels asynchrones mais les promesses sont plus pratiques : lorsqu'on crée une promesse avec la classe "promise", on lui associe implicitement une méthode "then" qui prend 2 arguments : une callback de succès et ensuite une callback d'erreur. Lorsque la promesse à réussit, c'est la callback de succès qui est appelée et si elle échoue, c'est la callback d'erreur qui est invoquée. ES6 permet d'améliorer la lisibilité avec les "arrow" fonction, elle sont très utilisée avec la programmation asynchrone car elles permettent de remplacer des fonctions anonymes omniprésentes dans les appels asynchrones en JavaScript avec une syntaxe plus élégante. Les promesses peuvent couvrir beaucoup de cas d'appels asynchrones, la gestion des événements mais elles ont leur limite surtout quand il faut gérer un grand nombre de requêtes dans un délai très court. Pour gérer proprement plusieurs événements qui peuvent arriver en parallèle sans saturer le code de promesse, il faut utiliser la programmation reactive.

## La programmation reactive 
C'est une nouvelle manière d'appréhender la programmation asynchrone et c'est l'avenir des applications modernes. Ce n'est pas nouveau, c'est une façon de concevoir une application : l'idée est de considérer les interactions qui se déroulent dans l'application comme des événements sur lequel on peut effectuer des opérations (regroupements, filtrage, combinaison). Les événements comme les clis de souris deviennent des flux d'événements asynchrones auxquels on peut s'abonner pour ensuite pouvoir y réagir. Il est possible de créer des flux à partir de tout et n'importe quoi et pas seulement des clics. Il est très fréquent de devoir réagir à des événements. Côté navigateur, en ajoutant des déclencheurs selon les interactions de l'utilisateur et côté serveur, en traitant des requêtes à la base de données ou à des services tiers. Dans la programmation reactive, toutes ces séquences d'événement sont des flux. La programmation réactive est une programmation avec des flux de données asynchrones. De manière générale, tous ces événements sont poussés par un producteur de données vers un consommateur. Il faudra définir des écouteurs d'événements, donc des consommateurs, sous forme de fonction pour réagir aux différents flux qui sont les producteurs de données. Les écouteurs d'événements sont des observeurs et le flux est le sujet observé (Observable). Lorsqu'on s'abonne à un flux pour capter ses événements, on dit que l'on s'inscrit ou s'abonne à ce flux. 

# Qu'est-ce qu'un flux  ?
https://rxmarbles.com/

C'est une séquence d'événements en cours qui sont ordonnés dans le temps, si on observe un utilisateurs qui clique plusieurs fois sur un bouton pour une raison quelconque, la succession des clics peut être modélisée comme un flux d'événements. On peut appliquer des opérations sur ce flux d'événement. Si on souhaite détecter les doubles clics de l'utilisateur et ignorer les clics simples, on va, pour cela, considérer qu'il y a un double clic s'il y a moins de 250 millisecondes d'écart entre 2 clics. On peut créer de fonction qui permettent de transformer un flux en un autre flux modifié. On regroupe des clics qui sont séparés par un délais de 250 millisecondes en un seul élément avec la fonction throttle, qui permet donc de transformer un flux initial en un nouveau nouveau flux selon des critères données. On applique la fonction map sur le flux de clics regroupés pour transformer chaque groupe en un entier qui correspond à la longueur de la liste. Un groupe de 2 clics vaut maintenant la valeur 2. Il ne reste plus qu'à filtrer des groupes dont la valeur n'est pas supérieur à2 car on veut les doubles clics. On considère comme un double clic tous les groupes de plus de deux clics, on applique un filtre sur le flux précédent avec la fonction "filter(x >=2)" et en seulement 3 opérations, on a obtenu le flux souhaité, on peut s'abonner à ce flux et réagir aux événements comme on le souhaite. Le flux sur lequel on a travaillé est simple mais les opérations utilisées peuvent aussi bien s'appliquer sur d'autres flux comme un flux de réponse à un serveur distant. Il existe plus d'opérations.

## La librairie RxJS 
On peut faire plus que s'abonner à un flux, les flux peuvent émettre 3 types de réponses différentes, pour chaque type de réponse, on peut définir la fonction "exécuter". Une fonction peut traiter les différentes valeurs de la réponse : un nombre, un tableau, des objets, etc, une fonction pour traiter le cas d'erreur et une fonction pour traiter le signal de fin, cela signifie que le flux est terminé et il n'y aura plus d'événement. Les événements du flux représentent soit les valeurs de la réponse en cas de succès, soit des erreurs ou alors des terminaisons, il n'y que 3 cas possibles. Pour faciliter l'implémentation de la programmation reactive, on utilise souvent des librairies spécifiques. La bilbiothèque la plus populaire pour l'ecosystème JavaScript est RxJS, c'est également celle qui a été choisie par l'équipe de développement d'Angular mais il existe d'autres librairies pour la programmation réactive.

## Les observables
Dans RxJS, un flux d'événement est représenté par un objet "Observable" qui sont très similaires à des tableaux, comme eux, ils contiennent une collection de valeurs, il ajoute juste la notion de valeur reportée dans le temps. Dans un tableau, toutes les valeurs sont disponibles immédiatemment, dans un Observable, les valeurs viendront au fur et à mesure, plus tard dans le temps. On peut traiter un Observable avec des opérateurs similaires à ceux des tableaux. La fonction "take" va récupérer les "n" premiers éléments d'un flux et se débarasser des autres : take(2) -> garder les deux premiers éléments du flux, les autres n'apparaissent plus dans le flux transformé. La fonction "map" applique la fonction passé en paramètre sur chaque événement et retourne le résultat. La fonction "filter" pêrmet de filtrer uniquement les événements qui répondent positivement au prédicat passé en paramètre. La fonction "merge" permet de fusionner deux flux : flux de sortie et aggrégation de deux flux passé en entrée. La fonction "subscribe" applique une fonction passée en paramètre à chaque événement reçu dans le flux, c'est cette fonction qu'on utilisera le plus souvent, elle accepte une deuxième fonction en paramètre consacrée à la gestion d'erreur et lorsque ce flux est terminé, il enverra un événement de terminaison qu'on peut détecter avec une troisème fontion. Un Observable est une simple collection asynchrone dont les événements arrivent au cours du temps. On peut construire des Observable depuis une requête Ajax, depuis un événement du navigateur, une réponse de websocket, une promesse, tout ce qui est asynchrone. La librairie qui forme le coeur d'Angular a un support basique pour les Observables, on est rapidement limité, il faut augmenter ce support avec des opérateurs et des extensions issus directement de librairie RxJS

## Choisir entre Observables et Promesse 
Les Observables sont différents des Promesse, même si il s'y ressemblent par certains aspects car ils gèrent tout deux des valeurs asynchrones, mais un Observable n'est pas quelque chose à usage unique, il continuera d'émettre des événements jusqu'à ce qu'il émette un événement de terminaison ou que l'on se désabonne de lui. Globalement, l'utilsation des Promesse et plus simple et dans de nombreux cas, c'est suffisant pour répondre aux besoins de l'application. Pour récupérer des données d'un serveur distant et les afficher à l'utilisateur, si on a besoin de faire qu'un seul appel, l'utilisation d'un Observable n'est pas forcément nécessaire. Il est possible de transformer un Observable en une promesse très simplement grâce à la méthode "toPromise" de RxJS. Plutôt que d'appliquer la méthode "subscribe" propre aux Observables, on pourra utiliser "then" propre au Promesses. Pour le moment, les Observables ne font pas partie de la spécification EcmaScript officielle mais cela pourrait être le cas dans le futur.

## Conclusion 
La programmation réactive permet d'élever le niveau d'abstraction du code et on doit moins se soucier de certains détails d'implémentation. Les applications web évoluent sans cesse et sont de plus en plus dynamique, l'édition d'un formulaire peut déclencher automatiquement une sauvegarde sur un serveur distant, un simple commentaire pour se répercuter directement sur l'écran de tous les utilisateurs connectés. En tant que développeur, il faut des outils pour gérer tout cela et le programmation réactive en fait partie.

## Les requêtes HTTP (amélioration de l'application "pokémon")
Pour l'instant, l'application est assez simple et permet seulement d'éditer des pokémon, on va vouloir communiquer avec un serveur distant pour récupérer les pokémons, les éditer, les supprimer et sauvegarder les changements sur le serveur. On pourrait aussi ajouter un champ de recherche sur la page d'accueil pour permettre de retrouver un pokémon plus facilement. Une API est une interface de communication, c'est ce qui permet de communiquer avec un service distant depuis une application, par exemple pour stocker les données sur un serveur distant de manière durable.

## HttpClientModule
Ce module permet de faire communiquer l'application Angular avec un serveur distant via le protocole HTTP, ce n'est pas un module de base d'Angular, il faut l'importer depuis la librairie "@angular/common/http". Le fichier "systemjs.config.js" est déjà configuré pour charger cette librairie et on peut l'importer depuis n'importe quel module de l'application. On le déclare dans la liste "imports" du module racine de l'application, on doit commencer par importer le nouveau module et ensuite, il faut l'ajouter en dessous du "BrowserModule", le module sera disponible partout dans l'application.

## Simuler un API web
Jusque maintenant, on récupérait les données depuis le service "pokemons.service" en utilisant le fait que l'instance de ce service soit unique à travers toute l'application mais ce système ne convient plus car on veut pouvoir communiquer avec un serveur distant. On ne dispose pas d'un serveur pour gérer les requêtes de l'application. On a un moyen de s'en sortir : Angular permet de simuler une API qui fonctionnera exactement comme si on utilisait un seveur distant, cette simulation est possible grace au module "HttpClientInMemoryWebApiModule" de la librairie "InMemoryWebAPI". Il faut déclarer l'API simulée auprès du reste de l'application, il est recommandé d'enregistrer les services globaux a toute l'application dans la liste import du module racine ("app.module.ts").

## L'option dataEncapsulation 
Elle permet de préciser le format des données renvoyées par l'API. On aurait pu encapsuler les données de réponse dans un objet avec une clé data.

## Méthode log appelée avec l'opérateur "tap" (pokemons.service.ts)
private log(log: string){
	console.info(log);
}

Méthode qui permet de centraliser la gestion des logs d'un service, si on souhaite, plus tard, archiver les logs plutôt que de les affichers dans la console, il suffira de modifier cette méthode.

## Gérer les erreurs
Il faut gérer les erreurs dans le cas ou la requête n'aboutirait pas. C'est une étape importante, il faut anticiper les erreurs HTTP, qui pourraient se produire pour des raisons indépendantes de notre volonté, c'est pour ça qu'il faut implémenter la méthode "handleError" qu'on va ajouter et qui est dédiée à la gestion des erreurs dans le service. La syntaxe "T" en TypeScript désigne le fait qu'on va typer un type en lui-même (number ou string). On utilise un nouvel opérateur of qui permet de transformer les données passées en paramètres en un Observable et ne pas interrompre le déroulement de tous les processus dans l'application, en cas d'erreur, on ne bloque pas le déroulement de l'application. Comme l'application est une démonstration, on se contente d'afficher une erreur dans la console. Dans le cas d'une application de production, on pourra mettre en place un système plus élaboré. Chaque méthode du service renvoie un Observable dont le résultat à un type différent. 

## Méthode getPokemon(id:number)
Méthode très similaire à "getPokemons", la seule différence est l'url utilisée et le type de retour, cette url retourne un seul pokémon et non un tableau de plusieurs pokémons, ensuite la méthode va retourner un seul pokémon au lieu d'un tableau de pokémon. Le service pokemon service renvoit un Observable et on doit mettre à jour tous les composants qui consomment ce service.

## Extraction de données
Comme on extrait, maintenant, les données à partir d'une API, si on veut persister les changements, on aura besoin de les écrire sur le serveur : faire une requête HTTP pour enregistrer les modifications. 

## Ajouter une méthode de modification dans pokemons.service
On a besoin d'une nouvelle méthode pour persister les modifications faites depuis le formulaire d'édition. La structure de la requête pour modifier un pokémon est similaire à une requête déjà vue, bien qu'on va utiliser une requête de type "put", c'est le type de requête qui est utilisé pour modifier une ressource afin de persister les changements côté serveur. Chaque requête HTTP contient un en-tête et un corps, il possible d'ajuster les deux en fonction des besoins de l'application.






























