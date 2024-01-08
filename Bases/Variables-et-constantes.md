# Variables et constantes

Cette page est, comme vous l'aurez compris, dédiée à la déclaration de variables et de constantes dans votre code

## `let`, `var` et autres péripéties

Le JavaScript contient une petite fonctionnalité plus ou moins sympathique en fonction du point de vue qui est le *typage dynamique*. Pas besoin de déclarer le type d'une variable avant de l'utiliser, et une variable peut même changer de type au cours de l'exécution d'un programme.

Cependant, contrairement à d'autres langages comme le Python il faut préalablement déclarer la variable avant de l'utiliser. Pour cela, nous avons 2 mots-clés à notre disposition : `var` et `let`. Voici un exemple :

```js
let x = 1, z = "abcd";
var tab = [1,4,6], a;
```

Nous avons créé ici 4 variables, dont 3 sont initialisées. Jusqu'ici, rien de très compliqué. Nous pouvons ensuite changer les valeurs de ces variables :

```js
x = 'acd';
z = 4.235
tab = PI;
a = new Map()
```

__Cependant__, il existe une différence entre `let` et `var`. Vous allez vous en rendre compte peu de fois en toute logique, mais elle existe tout de même : `var` est insensible au scoping dans une fonction, tandis que `let` y est soumis. Exemples :

```js
var test = 5; // Valide
var test = 7; // Valide aussi

let testLet = 5; // Valide
let testLet = 7; // Erreur : on ne peut pas définir 2 let dans le même scope avec le même nom
```

Autre exemple :

```js
function test(){
    if (true) {
        var varParam = 1;
        let letParam = 2;

        if(true) {
            console.log(varParam); // Affiche 1
            console.log(letParam); // Affiche 2
        }
    }

    console.log(varParam); // Affiche 1
    console.log(letParam); // Affiche une erreur : letParam non défini
}
```

Ainsi, cela peut avoir des effets inattendus lorsque l'on effectue des opérations avec plusieurs variables du même nom avec des scopes différents

Pour `var` :

```js
function testVar(){
    var x = 1;
    if (true) {
        var x = 2;
        console.log(x); // Affiche 2
    }
    console.log(x); // Affiche 2
}
```

Pour `let` :

```js
function testLet(){
    let x = 1;
    if (true) {
        let x = 2;
        console.log(x); // Affiche 2
    }
    console.log(x); // Affiche 1
}
```

Et si l'on combine les 2 :

```js
function testLetVar(){
    var x = 1;
    if (true) {
        let x = 2;
        console.log(x); // Affiche 2
    }
    console.log(x); // Affiche 1
}
```

Pour ces raisons, on va préferer utiliser `let` pour les variables d'itération, ou en général les variables temporaires utilisées dans les boucles, et `var` pour les variables destinées à être utilisées dans l'entièreté d'une fonction.

### Initialisation

Autre point important : les variables déclarées vides avec `var` sont initialisées en tant que `undefined`, tandis que celles déclarées vides avec `let` ne sont pas initialisées, on ne peut donc pas accéder à elles avant de leur attribuer une valeur d'abord

## Les constantes

On peut aussi déclarer une constante à l'aide du mot-clé `const` :

```js
const a = 5, j = ['a','b','c'];
```

Une fois qu'une constante est déclarée, il est impossible de la modifier, sinon l'interpréteur vous rendra une erreur. Il est de plus impossible de déclarer une constante sans l'initialiser à un valeur.

Cependant, si la constante est un objet, il est tout à fait possible de modifier ses propriétés et ses éléments, mais pas la constante en elle-même. Exemple :

```js
const obj = {
    a: 'xyz',
    b: 5
}

obj.a = 'abc'; // Valide
obj.b == 4; // Valide aussi, s'évalue en tant que `false`

obj = {
    a:'abc',
    b:3
}
// Invalide : obj ne peut pas être modifié directement
```

Les constantes sont déclarées dans un certain scope, comme les `let`, et ne peuvent en sortir :

```js
function testConst(){
    if(true) {
        const a = 3;
        console.log(a); // Affiche 3
    }

    console.log(a); // Affiche une erreur : a non déclarée
}
```

## Récapitulatif

- `var` est scope au niveau de la fonction ou global, `let` et `const` sont scope au niveau du bloc de code
- Dans le même scope : Une `const` ne peut être ni update ni redéclarée, une `let` peut être update mais pas redéclarée, une `var` peut être update et redéclarée
- `var` automatiquement initialisée à `undefined`, `let` nécessite une valeur avant utilisation mais peut être créée sans être initialisée, `const` renvoie une erreur si non initialisée

Voilà, c'est à peu près tout pour les variables & constantes !
