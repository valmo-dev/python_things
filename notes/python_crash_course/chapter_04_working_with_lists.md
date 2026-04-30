### Python Crash Course: Chapter 4 - Working with Lists

## Résumé

Le chapitre 4 t'apprend à travailler avec plusieurs éléments d'une liste, pas
seulement avec un élément isolé.

En JavaScript, tu utiliserais souvent `for...of`, `.map()`, `.filter()` ou
`.slice()`. En Python, tu vas surtout utiliser :

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(magician)
```

Dans ce chapitre, l'idée principale est d'apprendre à :

1. parcourir une liste avec une boucle `for`
2. comprendre l'indentation Python
3. générer des nombres avec `range()`
4. créer des listes numériques
5. utiliser les list comprehensions
6. extraire une partie d'une liste avec les slices
7. copier correctement une liste
8. utiliser les tuples pour des collections immutables
9. appliquer les premières règles de style PEP 8

## Les points importants

### 1. Parcourir une liste avec `for`

Une boucle `for` permet d'exécuter une action pour chaque élément d'une liste.

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(magician)
```

Lis cette boucle comme : "pour chaque `magician` dans `magicians`, affiche
`magician`."

Pont mental JS/PHP:

- JS : `for (const magician of magicians) { ... }`
- PHP : `foreach ($magicians as $magician) { ... }`
- Python : `for magician in magicians:`

Le nom temporaire doit représenter un seul élément :

```python
for cat in cats:
    print(cat)

for dog in dogs:
    print(dog)

for item in list_of_items:
    print(item)
```

La convention singulier/pluriel aide beaucoup à lire le code.

### 2. L'indentation définit le bloc

En Python, il n'y a pas d'accolades `{}` comme en JavaScript ou PHP.
L'indentation définit ce qui appartient à la boucle.

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(f"{magician.title()}, that was a great trick!")
    print(f"I can't wait to see your next trick, {magician.title()}.\n")
```

Les deux `print()` sont indentés, donc les deux sont exécutés pour chaque
élément de la liste.

Si une ligne n'est pas indentée, elle est exécutée après la boucle :

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(f"{magician.title()}, that was a great trick!")

print("Thank you, everyone. That was a great magic show!")
```

Ici, le dernier `print()` ne s'exécute qu'une seule fois.

### 3. Erreurs classiques d'indentation

Si tu oublies d'indenter après un `for`, Python lève une erreur :

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
print(magician)
```

Erreur :

```python
IndentationError: expected an indented block
```

Autre erreur plus dangereuse : oublier d'indenter une ligne qui devait être
dans la boucle.

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(f"{magician.title()}, that was a great trick!")
print(f"I can't wait to see your next trick, {magician.title()}.")
```

Ce code est valide, mais le second message ne s'affiche qu'une seule fois,
avec la dernière valeur de `magician`.

C'est une erreur logique, pas une erreur de syntaxe.

### 4. Ne pas oublier les deux-points

Une boucle `for` finit par `:`.

```python
for magician in magicians:
    print(magician)
```

Sans `:`, Python ne sait pas que la ligne suivante démarre un bloc.

```python
for magician in magicians
    print(magician)
```

Erreur :

```python
SyntaxError: expected ':'
```

### 5. Générer des nombres avec `range()`

`range()` génère une séquence de nombres.

```python
for value in range(1, 5):
    print(value)
```

Résultat :

```text
1
2
3
4
```

Important : la borne de fin est exclue.

Donc `range(1, 5)` signifie : de `1` jusqu'à `5`, mais sans inclure `5`.

Pour afficher `1` à `5`, il faut écrire :

```python
for value in range(1, 6):
    print(value)
```

Pont mental JS:

```js
for (let value = 1; value < 6; value++) {
  console.log(value)
}
```

Le `< 6` en JS correspond à l'exclusion de la borne finale en Python.

### 6. Créer une liste avec `range()` et `list()`

`range()` ne crée pas directement une liste affichable comme une liste normale.
Si tu veux une vraie liste, tu peux convertir avec `list()`.

```python
numbers = list(range(1, 6))
print(numbers)
```

Résultat :

```python
[1, 2, 3, 4, 5]
```

Tu peux aussi passer un troisième argument : le pas.

```python
even_numbers = list(range(2, 11, 2))
print(even_numbers)
```

Résultat :

```python
[2, 4, 6, 8, 10]
```

Ici :

- `2` : valeur de départ
- `11` : borne de fin exclue
- `2` : pas entre chaque valeur

### 7. Construire une liste avec une boucle

Tu peux partir d'une liste vide, puis ajouter des éléments avec `append()`.

```python
squares = []

for value in range(1, 11):
    square = value ** 2
    squares.append(square)

print(squares)
```

Résultat :

```python
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

`**` signifie puissance.

```python
square = value ** 2
cube = value ** 3
```

Tu peux aussi écrire plus court :

```python
squares = []

for value in range(1, 11):
    squares.append(value ** 2)
```

Le choix dépend de la lisibilité. Si la formule devient complexe, une variable
intermédiaire peut rendre le code plus clair.

### 8. Statistiques simples sur une liste de nombres

Python fournit quelques fonctions built-in pratiques.

```python
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]

print(min(digits))
print(max(digits))
print(sum(digits))
```

- `min()` : plus petite valeur
- `max()` : plus grande valeur
- `sum()` : somme des valeurs

Pont mental :

- JS n'a pas d'équivalent aussi direct sans `Math.min(...numbers)` ou `reduce()`
- PHP a `min($numbers)`, `max($numbers)`, `array_sum($numbers)`
- Python garde ça simple avec des fonctions built-in

### 9. List comprehensions

Une list comprehension permet de créer une liste en une ligne à partir d'une
boucle.

```python
squares = [value ** 2 for value in range(1, 11)]
print(squares)
```

C'est l'équivalent Python d'un `map()` simple en JavaScript.

Pont mental JS:

```js
const squares = numbers.map((value) => value ** 2)
```

Mais en Python, tu lis la ligne comme :

```python
[expression for item in iterable]
```

Exemple :

```python
cubes = [value ** 3 for value in range(1, 11)]
```

À ce stade, retiens surtout ceci :

- une boucle classique est plus explicite
- une list comprehension est plus concise
- si tu ne comprends pas la ligne en la relisant, garde la boucle classique

### 10. Slicing : extraire une partie d'une liste

Un slice permet de récupérer une partie d'une liste.

```python
players = ["charles", "martina", "michael", "florence", "eli"]

print(players[0:3])
```

Résultat :

```python
["charles", "martina", "michael"]
```

Comme avec `range()`, la borne de fin est exclue.

Donc `players[0:3]` récupère les index `0`, `1` et `2`.

Autres formes utiles :

```python
players[:4]   # du début jusqu'à l'index 4 exclu
players[2:]   # de l'index 2 jusqu'à la fin
players[-3:]  # les trois derniers éléments
```

Pont mental JS:

```js
players.slice(0, 3)
```

Même idée : début inclus, fin exclue.

### 11. Boucler sur une partie de liste

Tu peux utiliser un slice directement dans une boucle `for`.

```python
players = ["charles", "martina", "michael", "florence", "eli"]

print("Here are the first three players on my team:")

for player in players[:3]:
    print(player.title())
```

Python ne parcourt ici que les trois premiers éléments.

C'est utile pour :

- afficher les premiers résultats
- paginer des données
- traiter une liste par morceaux
- récupérer les meilleurs scores après un tri

### 12. Copier une liste correctement

Pour copier une liste, tu peux utiliser un slice complet.

```python
my_foods = ["pizza", "falafel", "carrot cake"]
friend_foods = my_foods[:]
```

Ici, `friend_foods` est une nouvelle liste.

```python
my_foods.append("cannoli")
friend_foods.append("ice cream")

print(my_foods)
print(friend_foods)
```

Résultat :

```python
["pizza", "falafel", "carrot cake", "cannoli"]
["pizza", "falafel", "carrot cake", "ice cream"]
```

Attention : ceci ne copie pas la liste.

```python
friend_foods = my_foods
```

Cette ligne crée une deuxième variable qui pointe vers la même liste.

Donc si tu modifies l'une, tu modifies l'autre :

```python
my_foods = ["pizza", "falafel", "carrot cake"]
friend_foods = my_foods

my_foods.append("cannoli")
friend_foods.append("ice cream")

print(my_foods)
print(friend_foods)
```

Les deux listes affichent les mêmes valeurs, parce qu'il n'y a en réalité
qu'une seule liste en mémoire.

Pont mental JS:

```js
const friendFoods = myFoods
```

Même problème : tu copies la référence, pas le tableau.

L'équivalent JS d'une vraie copie serait :

```js
const friendFoods = [...myFoods]
```

En Python, à ce stade du livre :

```python
friend_foods = my_foods[:]
```

### 13. Tuples : listes immutables

Un tuple ressemble à une liste, mais il ne peut pas être modifié après sa
création.

```python
dimensions = (200, 50)

print(dimensions[0])
print(dimensions[1])
```

Si tu essaies de modifier un élément :

```python
dimensions[0] = 250
```

Python lève une erreur :

```python
TypeError: 'tuple' object does not support item assignment
```

Utilise un tuple quand les valeurs ne doivent pas changer.

Exemples :

- dimensions fixes
- coordonnées simples
- options constantes
- valeurs groupées qui ne doivent pas être modifiées

Pont mental TypeScript : un tuple Python ressemble à une structure courte et
fixe, proche d'un tableau `readonly` dans l'intention.

### 14. Boucler sur un tuple

Tu peux parcourir un tuple comme une liste.

```python
dimensions = (200, 50)

for dimension in dimensions:
    print(dimension)
```

La différence n'est pas dans la lecture, mais dans la mutation :

- liste : mutable
- tuple : immutable

### 15. Réassigner un tuple

Tu ne peux pas modifier un élément d'un tuple, mais tu peux réassigner la
variable à un nouveau tuple.

```python
dimensions = (200, 50)
dimensions = (400, 100)
```

Tu ne changes pas le tuple original. Tu fais pointer `dimensions` vers un
nouveau tuple.

### 16. Style PEP 8

PEP 8 est le guide de style officiel Python.

À ce stade, retiens surtout :

- 4 espaces par niveau d'indentation
- éviter de mélanger tabs et spaces
- garder des lignes raisonnablement courtes
- utiliser des lignes vides pour séparer les blocs logiques
- ne pas abuser des lignes vides
- privilégier le code lisible au code compact

Important : Python utilise l'indentation pour comprendre le programme, donc
le style n'est pas seulement esthétique.

## Tableau mental à retenir

- `for item in items:` : parcourir une liste
- les lignes indentées appartiennent à la boucle
- les lignes non indentées après la boucle s'exécutent une seule fois
- `range(1, 6)` : nombres de `1` à `5`
- `range(2, 11, 2)` : nombres de `2` à `10`, par pas de `2`
- `list(range(...))` : convertir un `range` en liste
- `value ** 2` : carré
- `value ** 3` : cube
- `min(numbers)` : minimum
- `max(numbers)` : maximum
- `sum(numbers)` : somme
- `[value ** 2 for value in range(1, 11)]` : list comprehension
- `players[0:3]` : slice du début à l'index `3` exclu
- `players[:3]` : trois premiers éléments
- `players[-3:]` : trois derniers éléments
- `my_foods[:]` : copie complète d'une liste
- `(200, 50)` : tuple
- un tuple est immutable

## Différences utiles par rapport à JS/PHP

- Python remplace les accolades `{}` par l'indentation.
- `for item in items:` ressemble à `for...of` en JS et `foreach` en PHP.
- `range()` exclut la borne finale, comme une condition JS du type `i < max`.
- `slice` Python utilise aussi une fin exclue, comme `array.slice()` en JS.
- `friend_foods = my_foods` copie la référence, pas la liste.
- `friend_foods = my_foods[:]` crée une nouvelle liste.
- Les list comprehensions remplacent souvent des `map()` simples.
- Les tuples servent quand une collection ne doit pas être modifiée.
- `min()`, `max()` et `sum()` sont directement disponibles en built-in.

## Erreurs classiques

### Oublier l'indentation

```python
for pizza in pizzas:
print(pizza)
```

Correction : le corps de la boucle doit être indenté.

```python
for pizza in pizzas:
    print(pizza)
```

### Indenter une ligne qui devait être après la boucle

```python
for pizza in pizzas:
    print(f"I like {pizza} pizza.")
    print("I really love pizza!")
```

Ici, `"I really love pizza!"` est affiché pour chaque pizza.

Si tu veux l'afficher une seule fois :

```python
for pizza in pizzas:
    print(f"I like {pizza} pizza.")

print("I really love pizza!")
```

### Oublier que la borne de fin est exclue

```python
for value in range(1, 5):
    print(value)
```

Ce code n'affiche pas `5`. Il s'arrête à `4`.

### Copier une référence au lieu d'une liste

```python
friend_foods = my_foods
```

Cette ligne ne crée pas une nouvelle liste. Elle crée un deuxième nom pour la
même liste.

Pour copier :

```python
friend_foods = my_foods[:]
```

### Modifier un tuple

```python
dimensions = (200, 50)
dimensions[0] = 250
```

Un tuple est immutable. Si les valeurs doivent changer, utilise une liste.

## En une phrase

Le chapitre 4 t'apprend à traiter une liste comme une collection complète :
la parcourir, générer des valeurs, extraire des sous-listes, copier sans
partager la référence, et choisir entre liste mutable et tuple immutable.

## Mini fiche de révision

```python
magicians = ["alice", "david", "carolina"]

for magician in magicians:
    print(magician.title())

print("The loop is finished.")

numbers = list(range(1, 6))
even_numbers = list(range(2, 11, 2))

squares = []

for value in range(1, 11):
    squares.append(value ** 2)

cubes = [value ** 3 for value in range(1, 11)]

digits = [1, 2, 3, 4, 5]

smallest = min(digits)
largest = max(digits)
total = sum(digits)

players = ["charles", "martina", "michael", "florence", "eli"]

first_three = players[:3]
last_three = players[-3:]

for player in players[:3]:
    print(player.title())

my_foods = ["pizza", "falafel", "carrot cake"]
friend_foods = my_foods[:]

dimensions = (200, 50)

for dimension in dimensions:
    print(dimension)
```
