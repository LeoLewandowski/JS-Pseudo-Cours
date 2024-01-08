# Logique

Cette page est dédiée aux différentes propriétés et spécificités logiques dans le JS, car elles ne sont pas toujours très faciles à comprendre, et que certaines sont trop spécifiques pour être mises dans une autre page.

## Egalité

### Généralités sur l'égalité

Un tableau ne sera jamais strictement égal à quoi que ce soit, même à un autre tableau contenant les mêmes données que lui. Il en va de même pour un objet.

Cependant un tableau peut être approximativemment égal à `true` ou `false` tandis qu'un objet ne sera jamais approximativement égal à aucun des deux.

### Egalité stricte et égalité approximative

Le JS possède un opérateur assez peu commun le triple égal `===`, qui sert à vérifier une égalité stricte. L'opérateur classique `==` sert quant à lui à vérifier une égalité approximative

Chacun de ces opérateurs possède aussi son opérateur inverse d'inégalité, `!=` et `!==`

#### Egalité approximative

L'égalité approximative marche entre deux types d'objets différents, notamment :
  
- Un nombre et sa représentation sous forme de chaîne de caractères
- `null` et `undefined` sont tous deux égaux approximativements
- Un tableau vide ou une chaîne de caractères vide sont approximativements égaux à `false`, n'importe quel autre tableau ou chaîne de caractères seront approximativement égaux à `true`
- `false` est approximativement égal à 0 et '0', `true` à tous les autres nombres et leur représentation sous forme de chaîne de caractères

Exemples :

```js
1 == '1';
false == '0';
true == 1;
false == [];
undefined == null;
```

#### Egalité stricte

L'égalité stricte, cependant, n'admet pas la comparaison entre 2 types différents. Si les 2 élements dont on vérifie l'égalité sont de types différents, l'égalite vaut automatiquement `false`.

Ainsi, `false === 0` est faux, de même que `true === 1`.

A retenir : `undefined` et `null` ont chacun leurs types respectifs, ainsi `undefined === null` s'évalue en tant que false.

## Représentation sous forme de `string`
