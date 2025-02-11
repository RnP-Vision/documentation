# Documentation template Carbone RnP

## [Lien documentation Carbone](https://carbone.io/documentation.html)

## Sommaire
- [Documentation template Carbone RnP](#documentation-template-carbone-rnp)
  - [Lien documentation Carbone](#lien-documentation-carbone)
  - [Sommaire](#sommaire)
  - [Appeler le JSon](#appeler-le-json)
    - [Tips et astuces](#tips-et-astuces)
  - [Conditions](#conditions)
    - [Particularité des chaines de caractères :](#particularité-des-chaines-de-caractères-)
    - [Valeurs vides : `ifEM()`](#valeurs-vides--ifem)
    - [Valeurs non vides : `ifNEM()`](#valeurs-non-vides--ifnem)
    - [Egalité : `ifEQ(valeur)`](#egalité--ifeqvaleur)
    - [Non égalité : `ifNE(valeur)`](#non-égalité--ifnevaleur)
    - [Supérieur : `ifGT(valeur)`](#supérieur--ifgtvaleur)
    - [Supérieur ou égal : `ifGTE(valeur)`](#supérieur-ou-égal--ifgtevaleur)
    - [Inférieur : `ifLT(valeur)`](#inférieur--ifltvaleur)
    - [Inférieur ou égal : `ifLTE(valeur)`](#inférieur-ou-égal--ifltevaleur)
    - [Contient : `ifIN(valeur)`](#contient--ifinvaleur)
    - [Ne contient pas : `ifNIN(valeur)`](#ne-contient-pas--ifninvaleur)
    - [Egalité type : `ifTE(valeur)`](#egalité-type--iftevaleur)
  - [Combiner des conditions](#combiner-des-conditions)
    - [Condition ET condition : `and(valeur)`](#condition-et-condition--andvaleur)
    - [Condition OU condition : `or(valeur)`](#condition-ou-condition--orvaleur)
  - [Affichage d'une valeur selon conditionnement](#affichage-dune-valeur-selon-conditionnement)
    - [Si condition vraie : `show(valeur)`](#si-condition-vraie--showvaleur)
    - [Si condition fausse : `elseShow(valeur)`](#si-condition-fausse--elseshowvaleur)
  - [Cacher / Supprimer un/des éléments selon conditionnement](#cacher--supprimer-undes-éléments-selon-conditionnement)
    - [Cacher selon condition : `hideBegin()` \& `hideEnd()`](#cacher-selon-condition--hidebegin--hideend)
    - [Supprimer selon condition : `drop(valeur)`](#supprimer-selon-condition--dropvaleur)
  - [Images](#images)
    - [Image fixe](#image-fixe)
    - [Image dynamique](#image-dynamique)
  - [Boucles](#boucles)
    - [Boucles sur un tableau](#boucles-sur-un-tableau)
    - [Boucles sur un objet](#boucles-sur-un-objet)
    - [Boucles sur des images](#boucles-sur-des-images)
    - [Set d'une variable](#set-dune-variable)
  - [Fonctions](#fonctions)
    - [Setter/Modification temporaire du JSON `(:set)`](#settermodification-temporaire-du-json-set)
    - [Adition `(:add)`](#adition-add)
    - [Soustraction `(:sub)`](#soustraction-sub)
    - [Multiplcation `(:mul)`](#multiplcation-mul)
    - [Division `(:div)`](#division-div)
    - [Modulo `(:mod)`](#modulo-mod)
    - [Valeur absolue `(:abs)`](#valeur-absolue-abs)
    - [Arrondir un réel supérieur `(:ceil)`](#arrondir-un-réel-supérieur-ceil)
    - [Arrondir un réel inférieur `(:floor)`](#arrondir-un-réel-inférieur-floor)
    - [Longueur d'un tableau `(:len)`](#longueur-dun-tableau-len)
    - [Convertion en INT `(:int)`](#convertion-en-int-int)
    - [Convertion en STRING `(:toFixed)`](#convertion-en-string-tofixed)
    - [Convertion/Affichage argent](#convertionaffichage-argent)
    - [Format des dates](#format-des-dates)
    - [Fonctions sur les dates](#fonctions-sur-les-dates)
    - [Format des tableaux](#format-des-tableaux)
    - [Fonctions d'agrégation](#fonctions-dagrégation)
    - [Fonctions cumulatives](#fonctions-cumulatives)
  - [Les couleurs](#les-couleurs)
    - [Appliqué une couleur à une ligne](#appliqué-une-couleur-à-une-ligne)
    - [Couleur en fond `:color(row, background)`](#couleur-en-fond-colorrow-background)
    - [Remplacement de couleur dynamique](#remplacement-de-couleur-dynamique)
  - [Liens de la documentation entière](#liens-de-la-documentation-entière)

## Appeler le JSon

Example d'appel du JSon : `{d.variable}`

### Tips et astuces
* `{#myAlias = d.wheels} {d.name} need {$myAlias} wheels!`
  * Résultat = Cars need 4 wheels!
* `{#mealOf($weekday) = d[weekday = $weekday]} Tuesday, we eat {$mealOf(2).name}.`
  * Résultat = Tuesday, we eat fish.

## Conditions

### Particularité des chaines de caractères :

- Si la chaine est un mot unique, les guillemets `''` ne sont pas nécessaires
- Sinon, les guillemets `''` sont nécessaires

### Valeurs vides : `ifEM()`

Disponible pour :
  - Chaines de caractères
  - Tableaux
  - Objets

Pas testé sur :
  - Entier ( 0 )
  - Booléen ( false )

Examples :
  - Chaine de caractères: `{d.string:ifEM()}`
  - Tableau : `{d.array:ifEM()}`

### Valeurs non vides : `ifNEM()`

Disponible pour :
  - Chaines de caractères
  - Tableaux
  - Objets

- Pas testé sur :
  - Entier ( 0 )
  - Booléen ( false )

Examples :
  - Chaine de caractères: `{d.string:ifNEM()}`
  - Tableau : `{d.array:ifNEM()}`

### Egalité : `ifEQ(valeur)`

Disponible pour :
  - Chaines de caractères
  - Entiers
  - Décimaux
  - Booléens

Pas testé sur :
  - Tableaux
  - Objets

Examples :
  - Entier : `{d.entier:ifEQ(5)}`
  - Chaine de caractères : `{d.string.ifEQ(test)}` ( pas besoin de guillemets pour des mots seuls )
  - Booléen : `{d.bool:ifEQ(true)}`

### Non égalité : `ifNE(valeur)`

Disponible pour :
  - Chaines de caractères
  - Entiers
  - Décimaux
  - Booléens

Pas testé sur :
  - Tableaux
  - Objets

Examples :
  - Entier : `{d.entier:ifNE(5)}`
  - Chaine de caractères : `{d.string.ifNE(test)}` ( pas besoin de guillemets pour des mots seuls )
  - Booléen : `{d.bool:ifEQ(true)}`

### Supérieur : `ifGT(valeur)`

Disponible pour :
  - Entiers
  - Décimaux

Examples :
  - Entier : `{d.entier:ifGT(5)}`
  - Decimal : `{d.decimal:ifGT(5.6)}`

### Supérieur ou égal : `ifGTE(valeur)`

Disponible pour :
  - Entiers
  - Décimaux

Examples :
  - Entier : `{d.entier:ifGTE(5)}`
  - Decimal : `{d.decimal:ifGTE(5.6)}`

### Inférieur : `ifLT(valeur)`

Disponible pour :
  - Entiers
  - Décimaux

Examples :
  - Entier : `{d.entier:ifLT(5)}`
  - Decimal : `{d.decimal:ifLT(5.6)}`

### Inférieur ou égal : `ifLTE(valeur)`

Disponible pour :
  - Entiers
  - Décimaux

Examples :
  - Entier : `{d.entier:ifLTE(5)}`
  - Decimal : `{d.decimal:ifLTE(5.6)}`

### Contient : `ifIN(valeur)`

Disponible pour :
  - Chaines de caractères
  - Tableaux

Examples :
  - Chaine de caractères : `{d.string:ifIN(Tic)}`
  - Tableau : `{d.array:ifIN(5)}` ou `{d.array:ifIN(Tic)}`

### Ne contient pas : `ifNIN(valeur)`

Disponible pour :
  - Chaines de caractères
  - Tableaux

Examples :
  - Chaine de caractères : `{d.string:ifNIN(Tic)}`
  - Tableau : `{d.array:ifNIN(5)}` ou `{d.array:ifNIN(Tic)}`


### Egalité type : `ifTE(valeur)`

Disponible pour :
  - Entiers
  - Décimaux
  - Chaines de caractères
  - Tableaux
  - Objets
  - Booléens

Examples :
  - Entier : `{d.entier:ifTE(integer)}`
  - Décimal : `{d.decimal:ifTE(number)}`
  - Chaine de caractères : `{d.string:ifTE(string)}`
  - Tableau : `{d.array:ifTE(array)}`
  - Objet : `{d.objet:ifTE(object)}`
  - Booléen : `{d.bool:ifTE(boolean)}`

## Combiner des conditions

### Condition ET condition : `and(valeur)`

Examples :
  - `{d.entier:ifEQ(5):and(.string):ifNEM()}`
  - `{d.string:ifEM:and(.decimal):ifGTE(5.6)}`

Particularité :
  - Dans le and(), `.` référence l'objet utilisé précédemment dans le conditionnement

### Condition OU condition : `or(valeur)`

Examples :
  - `{d.entier:ifEQ(5):or(.string):ifNEM()}`
  - `{d.string:ifEM:or(.decimal):ifGTE(5.6)}`

Particularité :
  - Dans le or(), `.` référence l'objet utilisé précédemment dans le conditionnement

## Affichage d'une valeur selon conditionnement

### Si condition vraie : `show(valeur)`

Examples :
  - Pour un entier valant 5 `{d.entier:ifEQ(5):show('Condition vraie')}` -> Affiche 'Condition vraie'
  - Pour une chaine de caractères 'Test': `{d.string:ifNEQ(Test):show('Condition vraie')}` -> Affiche 'Condition vraie'

### Si condition fausse : `elseShow(valeur)`

Examples :
  - Pour un entier valant 5 `{d.entier:ifEQ(4):show('Condition vraie'):elseShow('Condition Fausse')}` -> Affiche 'Condition fausse'
  - Pour une chaine de caractères 'Test': `{d.string:ifNEQ(Machine):show('Condition vraie'):elseShow('Condition fausse')}` -> Affiche 'Condition fausse'

## Cacher / Supprimer un/des éléments selon conditionnement

### Cacher selon condition : `hideBegin()` & `hideEnd()`

Utilisation :

`hideBegin()` & `hideEnd()` permettent de délimiter respectivement le début et la fin pour cacher les éléments entre ces balises

![Example utilisation hide begin & hide end](hide.png)


### Supprimer selon condition : `drop(valeur)`

Valeurs disponibles :
  - p : supprime un paragraphe
  - row : supprime une ligne d'un tableau
  - img : supprime une image
  - table : supprime un tableau
  - chart : supprime un graphique
  - shape : supprime une forme ( rond, carré, flèche, etc...)
  - slide : supprime une slide ( powerpoint )
  - item : supprime un point d'une liste à points

Utilisation :

`drop(valeur)` permet de supprimer un élément désigné par la valeur dans le drop

![Example utilisation drop](drop.png)

## Images

### Image fixe

Insérer l'image directement dans la template

### Image dynamique

Insérer une image qui sert de `placeholder` et lui définir une `largeur`.
Il suffit ensuite de se rendre dans les `propriétés` de l'image et renseigner la variable contenant l'url : `{d.lienPhoto}` dans `Texte alternatif`

## Boucles

### Boucles sur un tableau

Utilisation :

Pour un tableau : [1, 6, 4, 6, 5]

- `{d.tableau[i]}` `{d.tableau[i+1]}`
  - Résultat : 1 6 4 6 5

Pour un tableau : [ {id: 6, nom: 'Ate'}, {id: 4, nom: 'Test'}, {id: 7, 'Ldao'} ]

- `{d.tableau[i].nom}` `{d.tableau[i+1]}`
  - Résultat : Ate Test Ldao

Pour un tableau : [ {id: 6, nom: 'Ate'}, {id: 4, nom: 'Test'}, {id: 7, 'Ldao'} ]

- `{d.tableau[id].nom}` `{d.tableau[id+1]}`
  - Résultat : Test Ate Ldao


Filtrer :

Pour un tableau : [ {id: 6, nom: 'Ate'}, {id: 4, nom: 'Test'}, {id: 7, 'Ldao'} ]

- `{d.tableau[i, id>5].nom}` `{d.tableau[i+1, id>5]}`
  - Résultat : Ate Ldao

Pour un tableau : [ {id: 6, nom: 'Ate'}, {id: 4, nom: 'Test'}, {id: 7, 'Ldao'} ]

- `{d.tableau[id, id>5].nom}` `{d.tableau[id+1, id>5]}`
  - Résultat : Ate Ldao

### Boucles sur un objet

Utilisation :

Pour un objet : { 'Cle1': 'Attribut1', 'Cle2': 'Attribut2', 'Cle3': 'Attribut3' }

- `{d.objet[i].att}` `{d.objet[i].val}`
  `{d.objet[i+1].att}` `{d.objet[i+1].val}`
  - Résultat :

    Cle1 Attribut1

    Cle2 Attribut2

    Cle3 Attribut3


### Boucles sur des images

Insérer deux image qui serviront de `placeholder` et leur définir une `largeur`.
Il faut ensuite se rendre dans les `propriétés` des images et renseigner la variable contenant l'url : `{d.tableau[i]}` `{d.tableau[i+1]}` dans `Description`

Fonctionne également avec les objets :
`{d.objet[i].val}` `{d.objet[i+1]}`

### Set d'une variable

`{d.variable:ifEQ(condition):show(True):elseShow(False):set(d.boolean)}`

La variable `d.boolean` contient désormais soit la valeur `True` soit la valeur `False` selon la condition

## Fonctions
### Setter/Modification temporaire du JSON `(:set)`
```JSON
{
  "cars": [
    { "qty" : 1 },
    { "qty" : 4 }
  ]
}
```
Exemple 1 : 
```
{d.cars[].qty:aggSum:set(c.mySum)}
Print stored value: {c.mySum}
```
Résultat 1 :
```
Print stored value: 5
```
---------------------
Exemple 2 :
```
{d.cars[].qty:append(' tyres'):set(.newInfo)}
JSON Modified
{d:printJSON}
JSON Usage
{d.cars[i].newInfo}
{d.cars[i+1].newInfo}
```
Résultat 2 :
```
JSON Modified
{
  "cars": [
    {"qty": 1, "newInfo": "1 tyres"},
    {"qty": 4, "newInfo": "4 tyres"}
  ]
}
JSON Usage
1 tyres
4 tyres
```

### Adition `(:add)`
```js
{d.subObject.qtyB:add(d.subObject.qtyC)} // (5 + 3) = 8 
```

### Soustraction `(:sub)`
```js
{d.subObject.qtyB:sub(d.subObject.qtyC)} // (5 - 3) = 2
```

### Multiplcation `(:mul)`
```js
{d.subObject.qtyB:mul(d.subObject.qtyC)} // (5 * 3) = 15
```

### Division `(:div)`
```js
{d.subObject.qtyB:div(d.subObject.qtyC)} // (10 / 2) = 5
```

### Modulo `(:mod)`
```js
{d.subObject.qtyB:mod(d.subObject.qtyC)} // (10 % 2) = 0
```

### Valeur absolue `(:abs)`
```js
{d.subObject.qtyB:mod(d.subObject.qtyC)} // |-10| = 10
```

### Arrondir un réel supérieur `(:ceil)`
```js
10.05123:ceil() // 11
1.05:ceil() // 2
-1.05:ceil() // -1
```

### Arrondir un réel inférieur `(:floor)`
```js
10.05123:floor() // 10
1.05:floor() // 1
-1.05:floor() // -2
```

### Longueur d'un tableau `(:len)`
### Convertion en INT `(:int)`
### Convertion en STRING `(:toFixed)`
### Convertion/Affichage argent
- `:formatC(precisionOrFormat, targetCurrency)`
  ```js
  '1000.456':formatC() // "1 000,46 €"
  ```

- `:convCurr(target, source)`
  ```js
  10:convCurr() // 20
  1000:convCurr() // 2000
  1000:convCurr('EUR') // 1000
  1000:convCurr('USD') // 2000
  1000:convCurr('USD', 'USD') // 1000
  ```

### Format des dates
```js 
// With API options: {
//   "lang": "fr",
//   "timezone": "Europe/Paris"
// }
'2017-05-10T15:57:23.769561+03:00':formatD('LLLL') // "mercredi 10 mai 2017 14:57"
'2017-05-10 15:57:23.769561+03:00':formatD('LLLL') // "mercredi 10 mai 2017 14:57"
'20160131':formatD('LLLL') // "dimanche 31 janvier 2016 00:00"
'20160131':formatD('dddd') // "dimanche"
'20160131':formatD('dddd', 'YYYYMMDD') // "dimanche"
1410715640:formatD('LLLL', 'X') // "dimanche 14 septembre 2014 19:27"
```

### Fonctions sur les dates
 * `:addD(amount, unit, patternIn)` {Ajouter un jour à la date}
 * `:subD(amount, unit, patternIn)` {Supprimer un jour à la date}
 * `:diffD(toDate, unit, patternFromDate, patternToDate)` {Calculer la différence entre deux date}
 * :convDate(patternIn, patternOut) {Convertit une date en un autre format}
 * Pour plus de précision : [Carbone date](https://carbone.io/documentation/design/formatters/date.html#addd-amount-unit-patternin)

  - ### Intervale et durée
    - `:formatI(patternOut, patternIn)`
    - Pour plus de précision : [Carbone intervale](https://carbone.io/documentation/design/formatters/interval.html)

### Format des tableaux
* `:arrayJoin(separator, index, count)`
  * Exemples : 
    ```js
      ['homer','bart','lisa']:arrayJoin() // "homer, bart, lisa"
      ['homer','bart','lisa']:arrayJoin(' | ') // "homer | bart | lisa"
      ['homer','bart','lisa']:arrayJoin('') // "homerbartlisa"
      [10,50]:arrayJoin() // "10, 50"
      []:arrayJoin() // ""
      null:arrayJoin() // null
      {}:arrayJoin() // {}
      20:arrayJoin() // 20
      undefined:arrayJoin() // undefined
      ['homer','bart','lisa']:arrayJoin('', 1) // "bartlisa"
      ['homer','bart','lisa']:arrayJoin('', 1, 1) // "bart"
      ['homer','bart','lisa']:arrayJoin('', 1, 2) // "bartlisa"
      ['homer','bart','lisa']:arrayJoin('', 0, -1) // "homerbart"
      ```
* `:arrayMap(objSeparator, attSeparator, attributes)`
  * Exemples : 
    ```js
    [{'id':2,'name':'homer'},{'id':3,'name':'bart'}]:arrayMap() // "2:homer, 3:bart"
    [{'id':2,'name':'homer'},{'id':3,'name':'bart'}]:arrayMap(' - ') // "2:homer - 3:bart"
    [{'id':2,'name':'homer'},{'id':3,'name':'bart'}]:arrayMap(' ; ', '|') // "2|homer ; 3|bart"
    [{'id':2,'name':'homer'},{'id':3,'name':'bart'}]:arrayMap(' ; ', '|', 'id') // "2 ; 3"
    [{'id':2,'name':'homer','obj':{'id':20},'arr':[12,23]}]:arrayMap() // "2:homer"
    ['homer','bart','lisa']:arrayMap() // "homer, bart, lisa"
    [10,50]:arrayMap() // "10, 50"
    []:arrayMap() // ""
    null:arrayMap() // null
    {}:arrayMap() // {}
    20:arrayMap() // 20
    undefined:arrayMap() // undefined
    ```
* `:count(start)`

### Fonctions d'agrégation
* `:aggSum` : Calcule la somme de toutes les valeurs d'un ensemble de données.
* `:aggAvg` : Calcule la moyenne des valeurs d'un ensemble de données.
* `:aggMin` : Trouve la valeur minimale dans un ensemble de données.
* `:aggMax` : Trouve la valeur maximale dans un ensemble de données.
* `:aggCount` : Compte le nombre total d'éléments dans un ensemble de données.
* `:aggCountD` : Compte le nombre d'éléments distincts dans un ensemble de données.
* `:aggStr` : Concatène toutes les chaînes de caractères d'un ensemble de données en utilisant un séparateur spécifié.
* `:aggStrD` : Concatène les chaînes de caractères distinctes d'un ensemble de données en utilisant un séparateur spécifié.


### Fonctions cumulatives
* `:cumSum` : Calcule la somme cumulée (totaux progressifs) d'un ensemble de données.
* `:cumCount` : Attribue un numéro séquentiel à chaque ligne d'une liste.
* `:cumCountD` : Attribue un numéro séquentiel à chaque élément distinct d'une liste.

Plus de précision sur ces fonctions : [Carbone aggrégations](https://carbone.io/documentation/design/computation/aggregation.html)

## Les couleurs
```js
{
  "test"      : "OK",
  "testError" : "ERROR",
  "success"   : "#007700",
  "error"     : "#FF0000"
}
```
```
The assessment passed
{d.test:ifEQ(OK):show(.success):elseShow(.error):color(p)}
Error color
{d.testError:ifEQ(OK):show(.success):elseShow(.error):color(p)}
```

### Appliqué une couleur à une ligne
```js
{
  "error": "#FF0000",
  "tests": [
    { "name": "Security Training","result": "ok" },
    { "name": "Code Auditing","result": "20 Vulnerabilities found" },
    { "name": "Firewall Testing","result": "ok" }
  ]
}
```
Exemple : 
  |Test|Info|
  -----|-----
  {d.tests[i].name}	{d.tests[i].result} | {d.tests[i].result:ifEQ(ok):show(#007700):elseShow(d.error):color(row, text)}
  {d.tests[i+1]}

Résultat : 
  |Test|Info|
  -----|-----
  <span style="color:green">Security Training |	<span style="color:green">ok 
  <span style="color:red">Code Auditing	| <span style="color:red">20 Vulnerabilities found 
  <span style="color:green">Firewall Testing | 	<span style="color:green">ok 

### Couleur en fond `:color(row, background)`
### Remplacement de couleur dynamique
`{bindColor(myColorToBind, myFormat) = d.myVar}`
```js
{
  "color": "#FF0000", // red
  "color2": "#00FF00", // green
  "color3": "#0000FF" // blue
}
```
<span style="color:cyan">Manage <span style="color:pink">dynamic <span style="color:yellow">color ! 
```
{bindColor(00FFFF, #hexa) = d.color}
{bindColor(FF00FF, #hexa) = d.color2}
{bindColor(FFFF00, #hexa) = d.color3}
```
Résultat :
<span style="color:red">Manage <span style="color:green">dynamic <span style="color:blue;">color ! 

## [Liens de la documentation entière](https://carbone.io/documentation/design/overview/getting-started.html)