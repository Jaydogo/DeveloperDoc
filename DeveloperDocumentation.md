# Developer Documentation !

## LIENS

- https://codepen.io/
- https://jsfiddle.net/
- https://pastebin.com/
- https://www.youtube.com/watch?v=Ukg_U3CnJWI
- http://lorempicsum.com/#rio
- https://scratch.mit.edu/projects/201657672/#editor
- https://github.com/h5bp/Front-end-Developer-Interview--Questions/blob/master/questions/general-questions.md
- http://cssnext.io/
- https://stackoverflow.com/
- https://www.w3schools.com/
- https://css-tricks.com/

# BEM

La méthodologie BEM est une solution élaborée par Yandex et publiée en 2010. BEM a deux faces : il s'agit d'abord d'une méthode déclarative de l'interface utilisateur servant à décrire un « arbre BEM », les outils  _open source_  de Yandex travaillent ensuite sur cet arbre. BEM apporte également une convention de nommage des classes CSS qui a gagné une certaine popularité. C'est de cette méthodologie du nommage, véritablement puissante, que nous allons parler ici.

BEM est l'acronyme de  _Block, Element, Modifier_, et toute la méthodologie du nommage à la manière BEM tient dans ces trois mots. La force du concept ? Ce qui compose un page ou une application Web peut toujours être rangé dans une arborescence de blocs, d'éléments et de modificateurs.

Un  **bloc**  est une entité indépendante, une « brique » de l'application ou de la page Web. Un bloc forme son propre contexte autonome. Ci-dessous des exemples de blocs dans une illustration tirée du site officiel :

![blocs BEM [source :  [bem.info](http://bem.info/method/definitions/#Unified-Data-Domain)]](https://www.alsacreations.com/xmedia/doc/original/bem-blocks-540.jpg)

Un **élément** est une partie d'un bloc. Le contexte d'un élément est celui du bloc. Ci-dessous deux exemples empruntés toujours au site officiel :

![](https://www.alsacreations.com/xmedia/doc/original/bem-elements-540.jpg)

En tant que « brique de construction », un bloc est réutilisable dans d'autres blocs ou dans des éléments. Il ne connait toutefois que son propre contexte et non celui du parent. Un bloc n'est donc pas livré avec les règles CSS de son propre positionnement au sein du conteneur parent. Nous éclaircirons ultérieurement, sur un cas d'utilisation, ce point important.

Un  **modificateur**  est une propriété qui sert à créer des variantes, pour faire des modifications minimes comme changer des couleurs. Il existe des modificateurs de blocs et des modificateurs d'éléments.

La méthodologie BEM établit ensuite trois règles essentielles :

1.  Les blocs et les éléments doivent chacun avoir un nom unique, lequel sera utilisé comme classe CSS ;
2.  Les sélecteurs CSS ne doivent pas utiliser les noms des éléments HTML (pas de  `.menu td`) ;
3.  Les cascades dans les sélecteurs CSS devraient être évitées.

À propos de la première règle, précisons que les identifiants HTML (les attributs  `id`) ne doivent pas être utilisés en CSS, chaque bloc pouvant par principe être instancié plusieurs fois. Les identifiants HTML ne servent que d'ancres. La deuxième règle est nécessaire dans la mesure où les blocs peuvent être imbriqués. Un sélecteur  `.menu td`  briserait la séparation des contextes en interagissant avec les balises  `<td>`  des sous-blocs, cela doit être évité.

Ces règles impliquent de préfixer les noms des éléments par leur contexte. Venons-en à la convention de nommage des classes CSS. Le site officiel prend soin de préciser que seuls comptent les concepts, la syntaxe restant libre. L'équipe de BEM utilise pour sa part une syntaxe à base de  _underscores_ :

-   `block-name`
-   `block-name_modifier_name`
-   `block-name__element-name`
-   `block-name__element-name_modifier_name`

Pouah ! Hideux ! La raison d'une telle laideur est un manque de caractères utilisables dans les identifiants en CSS.

Le code CSS, en méthodologie BEM, est presque plat. Voici un exemple de code CSS pour un bloc  `search-box`  doté d'un modificateur  `light`, contenant un élément  `btn`  avec un modificateur  `max_visible` :

```css
.search-box {
  height: 300px;
  width: 300px;
}
.search-box_light {
  background-color: #DEF;
  color: #777;
}
.search-box__btn {
  padding: 4px;
}
.search-box__btn_max_visible {
  font-weight: bold;
}
```

Le code HTML :

```html
<div class="search-box search-box_light">
  <!-- (input field here) -->
  <button class="search-box__btn search-box__btn_max_visible">Search</button>
</div>
```
Une cascade est utilisée lorsqu'un modificateur de bloc a un effet sur un élément :
```css
.search-box_light .search-box__btn {
  background-color: #9AB;
}
```
Signalons entre parenthèses que cette cascade est à éviter sur les blocs pouvant s'imbriquer récursivement, car le modificateur du bloc parent affecterait alors les blocs enfants. Fort heureusement le cas est rare.

## FLEXBOX GRID

Il ne faut pas confondre FlexboxGrid et CSS grid. Le nombre maximum de colonne est de 12. Ces grilles permettent de se repéré sur Sketch. Dans une ligne on peut déclaré autant de colonne que l'on veux. Il existe deux types de container le classique (container) et le fluid. Les 12 colonnes prennent la taille du container. Il est possible de faire des grilles dans des grilles (Nested Grids = voir site FlexboxGrid). On peut également ajouter des offset : permet de dire au colonne de commencer a partir de la colonne que l'on veux. On décale ainsi de deux colonnes.

Taille :

xs = mobile  
sm = small (petite tablette)  
md = medium ( tablette )  
lg = large ( desktop)  
row= lignes  
col= colonnes
```
<div class="container">

<div class="row">

  <div class="col-xs-12 col-md-6 col-lg-3"></div>
  <div class="col-xs-12 col-md-6 col-lg-3"></div>
  <div class="col-xs-12 col-md-6 col-lg-3"></div>
  <div class="col-xs-12 col-md-6 col-lg-3"></div>
  <div class="col-xs-12 col-md-6 col-lg-3"></div>
  <div class="col-xs-12 col-md-6 col-lg-3"></div>

</div>

</div>


<div class="row between-xs"> /* ceci signifie qu'à partir de la taille xs, donc mobile, toute les colonnes
```
## GRID LAYOUT

Cette technologie permet de créer une grille en fonction des éléments que l'on souhaite placé dans notre page. On définit le nombre de colonnes que l'on souhaite ainsi que le nombre de lignes. Par exemple si on souhaite 3 colonnes de 234px chacune et 4 lignes de 125px, avec un espacement de 2rem alors on écrit :
```
.container {
 display: grid;
 grid-template-columns: 234px 234px 234px;
 grid-template-rows: 125px 125px 125px 125px;
 grid-gap: 2rem;
}

```
Cela nous permet d'obtenir une grille aux dimensions que l'on souhaite. Ainsi on peut placé nos éléments en fonction de celle-ci.Prénons l'exemple d'une image que l'on souhaite placé sur la premiére colonne à la deuxiéme ligne.
```
.img1{
grid-column: 1 / 2;
grid-row: 2/ 4 ;
 width : 235px;
 height: 350px;
}
```
## FONT FACE

La règle  **@font-face**  permet de définir les polices d'écriture à utiliser pour afficher le texte de pages web. En permettant aux développeurs de fournir leurs propres polices, il n'est plus nécessaire de dépendre uniquement des polices qui sont installées sur les postes des utilisateurs. Le but du  **@font-face**  est de permettre au développeur d’utiliser une font non conventionnelle qui n’est hébergé dans aucun service webfont, en lui permettant de l’héberger en même temps que notre site. Ainsi on est sûr que l’utilisateur pourra la visualiser. On crée ainsi ce que l’on appelle une police distante.

-   **Etape 1 :**

Pour intégrer une typographie personnalisé il faut s’assurer que la typographie utilisé est de format:

.ttf : True Type .otf : OpenType

-   **Etape 2 :**

On télécharge la police qui nous intéresse. J’utilise le site : fontsquirrel.com afin de trouver une typographie gratuite. Pour l’exemple j’ai télécharger la typographie Fira Sans.

-   **Etape 3:**

Ensuite j’utilise le générateur Font Squirrel fin d’obtenir ma police en quatre formats différents : eot , svg, ttf, et woof. Cette étape sert à s’assurer que la police sera utilisable pour tout les navigateurs.

-   **Etape 4 :**

Je transfert ma font dans mon dossier dev-absolute, dans le dossiers font afin qu’elle se trouve dans le même dossier que ma feuille de style.

-   **Etape 5 :**

Dans mon dossier font, j’obtient donc 1 fichier css (feuille de style) ainsi que 4 fichiers de typographie (eot , svg, ttf, et woof). Ainsi je peux ouvrir ma feuille de style dans mon éditeur de texte, ce qui va me permettre d’obtenir le code  **@font-face**  de chacune de mes quatre polices.
```
@font-face{
  font-family: 'fira_sans_bold';
  src : url('firasans_bold-webfont.woff2') format('woff2'),
        url('firasans_bold-webfont.woff2') format('woff2');
  font-weight : normal;
  font-style: normal;
}
```
Je peux par conséquent copiez le code dans mon fichier css principal et supprimer ma feuille de style. Il va néanmoins falloir modifier ma source en fonction de la position de mon dossier afin d’indiquer le bon « chemin »

```
  url('../fonts/firasansot-bold-webfont.svg#fira_sans_otbold')

```

J’utilise les « .. /» afin de sortir du dossier css et d’entrer dans le dossier font

-   **Etape 6:**

Grâce à cette démarche nous avons dorénavant la possibilité d’utilisé les attribut suivant dans notre css :

font-family : désignant la police (‘Fira Sans’) font-weight : désignant la graisse de la police (bold,normal,lighter) font-style : désignant le style de la police: normal, oblique, italique
```
.name{
  font-family: 'Fira Sans';
  font-weight: bold;
  font-style: oblique;
}
```
## SCSS

-   ### Variables
    

Les variables permettent de stocker des informations afin de pouvoir les réutilisé plus tars dans la feuille de style. Cela permet d'optimisé notre style car en effet une couleur utilisé souvent dans notre style peut être modifier partout en un seul geste. Les variables sont précédé d'un $.

->  _CSS_
```
body {
  font-family: Helvetica, sans-serif;
  color: #333;
}
```
->  _SCSS_
```
$font-stack:    Helvetica, sans-serif;
$primary-color: #333;

body {
  font-family: $font-stack;
  color: $primary-color;
}
```
-   ### Nesting
    

Le Nesting permet de respecter la hiérarchie du HTML.

->  _CSS_
```
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav li {
  display: inline-block;
}

nav a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```
->  _SCSS_
```
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```
-   ### Les imports
    

->  _RESET_
```
/* _reset.scss */

html,
body,
ul,
ol {
  margin:  0;
  padding: 0;
}
```
->  _CSS_
```
/* base.scss */

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```
->  _SCSS_
```
html, body, ul, ol {
  margin: 0;
  padding: 0;
}

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```
-   ### Les Mixins
    

Une mixin permet de regrouper le style d'un élément et de l'appeler lorsqu'on en as besoin. Ainsi cela permet de ne pas réecrire le style pour un même élément comme pour des bouttons. Cela permet d'optimiser notre code.

->  _CSS_
```
.button {
  padding: 14px 0;
  min-width: 100%;
  display: inline-block;
  border-radius: 4px;

  outline: none;
  cursor: pointer;
  background: #4D61D6;
  color: #fff;
  font-size: 14px;
  font-weight: 300;
  text-align: center;
  letter-spacing: .9px;
  transition: background .3s ease;
}
```
->  _SCSS_
```
@mixin generic-button {
  padding: 14px 0;
  min-width: 100%;
  display: inline-block;
  border-radius: 4px;

  outline: none;
  cursor: pointer;
  background: #4D61D6;
  color: #fff;
  font-size: 14px;
  font-weight: 300;
  text-align: center;
  letter-spacing: .9px;
  transition: background .3s ease;
}

button {
  @include generic-button;
}
```
### SVG :

-   svg : l'attribut fill permet de remplir l'image de couleur cela évite d'avoir à l'importer de toute les couleurs.

### CSS Tips:

**=> Box-sizing :**  

-   border-box

Permet de ne pas augmenter la taille d'une div. Si on as une div de 300px et qu'on veux un padding de 20px partout. On va utiliser box-sizing:borderbox pour ajouter les 20px de padding sans changer la taille de la div initiale. Quand vous ajoutez la propriété box-sizing: border-box; à un élément, le paddinget la bordure de cet élément n'augmentent plus sa largeur.

border-box indique au navigateur de prendre en compte la bordure et le remplissage dans la valeur définie pour la largeur et la hauteur. Autrement dit c'est le contenu de la boîte qui sera compressé pour absorber cette largeur supplémentaire.

-   content-box

content-box est la valeur par défaut et correspond au comportement par défaut. Si on définit un élément avec une largeur de 100 pixels, la boîte de contenu de cet élément mesurera 100 pixels de large et la largeur de la bordure et/ou du remplissage sera alors ajoutée pour constituer la largeur finalement affichée.

**=> Direction:**

Permet de modifier la direction d'un texte ou d'un élément.

-   ltr

La valeur par défaut qui correspond à une disposition de la gauche vers la droite pour le texte et les autres éléments.

-   rtl

Le texte et les autres éléments vont de la droite vers la gauche.

**=> Position :**

-   Static

static est la valeur par défaut de tous les éléments. Un élément avec position: static; n'est positionné d'aucune manière spéciale. Un élément static est dit non positionné et un élément avec une propriété position ayant une valeur autre que static est dit positionné.
```
.static {
  position: static;
}
```
-   Fixed

Un élément positionné en fixed est positionné par rapport a la fenêtre du navigateur, ce qui signifie qu'il reste toujours à la même place même si la page défile. De la même manière qu'avec un élément positionné en relative, nous pouvons utiliser les propriétés top, right, bottom et left. Lorsqu'on met une div en fixed alors il faut utiliser un z-index sur toutes les autres div car fixed sort la div du flux.
```
.fixed {
  position: fixed;
  bottom: 0;
  right: 0;
  width: 200px;
  background-color: white;
}
```
-   Relative

relative se comporte de la même façon que static sauf si on ajoute quelques propriétés en plus. Avec les propriétés top, right, bottom et left un élément positionné en relative va le placer ailleurs que sa position normale. Le reste du contenu ne sera pas ajusté pour prendre la place dans l'espace laissé par l'élément.
```
.relative1 {
  position: relative;
}
.relative2 {
  position: relative;
  top: -20px;
  left: 20px;
  background-color: white;
  width: 500px;
}
```
-   Absolute

absolute se comporte comme fixed sauf que son positionnement est relatif à l'élément parent positionné le plus proche au lieu d'être relatif à la fenêtre du navigateur. Si un élément positionné en absolute n'à aucun élément parent positionné, il utilise le corps du document et se déplace avec le document au défilement de la page.
```
.relative {
  position: relative;
  width: 600px;
  height: 400px;
}
.absolute {
  position: absolute;
  top: 120px;
  right: 0;
  width: 300px;
  height: 200px;
}
```
## STARER

  
https://github.com/davidvenin/parcel-starter

# RESET CSS


```
html, body, div, span, applet, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, 
abbr, acronym, address, big, cite, code, del, dfn, em, img, ins, kbd, q, s, samp, small, strike, strong,
sub, sup, tt, var, b, u, i, center, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody,
tfoot, thead, tr, th, td, article, aside, canvas, details, embed, figure, figcaption, footer, header,
hgroup, menu, nav, output, ruby, section, summary, time, mark, audio, video { margin: 0; padding: 0;
border: 0; font-size: 100%; font: inherit; vertical-align: baseline; } /* HTML5 display-role reset for
older browsers */ article, aside, details, figcaption, figure, footer, header, hgroup, menu, nav, section
{ display: block; } body { line-height: 1; } ol, ul { list-style: none; } blockquote, q { quotes: none; }
blockquote:before, blockquote:after, q:before, q:after { content: ''; content: none; } table { border
-collapse: collapse; border-spacing: 0; }
```


