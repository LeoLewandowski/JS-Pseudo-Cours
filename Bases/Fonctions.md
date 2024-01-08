# Fonctions

Cette page présentera les fonctions en JS, les différentes façons de les déclarer, les types de fonctions, et la définition de leurs paramètres.

__Cette page NE TRAITERA PAS des fonctions asynchrones__ ; je ferai peut-être une autre page dessus plus tard, mais ce n'est pas prévu pour le moment.

## Déclaration de fonctions

Comme pour les variables, il y a plusieurs moyens de déclarer des fonctions en JS. Cependant pas de panique ! Il n'y a aucune différence d'utilisation entre les définitions de fonctions, contrairement aux variables.

La définition la plus simple est la suivante :

```js
function func(/* arguments */) {
    // Code ici
}
```

Ensuite viennent les fonctions lambdas :

```js
var func = function(/* arguments */) {
    // Code ici
}
```

Et une deuxième écriture de fonction lambda (aussi appelée "arrow functions") :

```js
var func = (/* arguments */) => {
    // Code ici
}
```

En JS Web vous serez amenés à utiliser beaucoup de fonctions lambda, c'est pourquoi je vous conseille de choisir une des deux écritures de fonctions lambda (les arrow functions sont le plus courant), et de toute les définir dans cette écriture, afin d'éviter de vous perdre entre les deux.

## Paramètres

Comme dans tous les languages, les fonctions en JS acceptent des paramètres. Cependant, le type de ces paramètres n'est pas défini, et tous les paramètres ne sont pas obligatoires.

### Paramètres positionnels

On peut passer plus de paramètres positionnels à une fonction que ce qu'elle n'accepte, les paramètres en trop seront tout simplement ignorés.

On peut aussi passer moins d'arguments à une fonction qu'elle ne demande, les paramètres non définis seront initialisés à undefined

Pour définir des paramètres positionnels, on doit leur donner un nom dans la définition de la fonction, comme ceci :

```js
function test(a, b, c){
    // Blablabla
}
```

On peut définir par ailleurs une valeur par défaut pour ces paramètres, au cas où ils ne sont pas précisés :

```js
function test(a, b = 'abc', c = 5, d){
    // Code
}
```

### Paramètres reste

On peut aussi passer ce que l'on appelle des paramètres reste à une fonction. Les paramètres reste acceptent un nombre infini de paramètres, et se retrouvent sous la forme d'un tableau :

```js
function test(...args){
    console.log(args);
}

test(1,3,5,2); // Sortie : [1, 3, 5, 2]
test();     // Sortie []
```

> Note : La notation spread (syntaxe `...`) est utilisable pour tous les objets itérables, pas seulement les paramètres reste, mais est utilisée un peu différemment dans les autres cas. On le verra plus tard

On peut aussi combiner les deux types de paramètres :

```js
function test(a, b = 5, ...c){
    // Code ici
}
```

*__CEPENDANT !!! Il ne peut y avoir qu'un seul paramètre de reste dans chaque fonction, et il doit toujours être situé à la fin de la liste de paramètres__*
