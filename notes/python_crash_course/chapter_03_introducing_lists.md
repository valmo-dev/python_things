### Python Crash Course: Chapter 3 - Introducing Lists

## Résumé

Une `list` Python est l'équivalent d'un tableau JavaScript ou d'un array indexé PHP.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
```

Dans ce chapitre, l'idée principale est d'apprendre à manipuler une liste proprement :

1. accéder aux éléments
2. ajouter ou supprimer des éléments
3. trier ou inverser une liste
4. connaître sa taille
5. éviter les erreurs d'index

## Les points importants

### 1. Indexation

Python commence à l'index `0`, comme JavaScript.

```python
motorcycles = ["honda", "yamaha", "suzuki"]

print(motorcycles[0])
print(motorcycles[1])
print(motorcycles[-1])
```

- `motorcycles[0]` : premier élément
- `motorcycles[-1]` : dernier élément
- l'index négatif est très idiomatique en Python

Pont mental JS/PHP:

- JS : `motorcycles[0]`
- PHP : `$motorcycles[0]`
- Python : même idée, mais `-1` pour le dernier élément est beaucoup plus courant

### 2. Modifier un élément

Une liste est mutable. Tu peux remplacer une valeur à une position donnée.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
motorcycles[0] = "ducati"
```

Comme en JS, tu modifies le contenu existant au lieu de recréer toute la structure.

### 3. Ajouter des éléments

```python
motorcycles = ["honda", "yamaha", "suzuki"]

motorcycles.append("ducati")
motorcycles.insert(0, "bmw")
```

- `append()` ajoute à la fin
- `insert(index, valeur)` insère à une position précise

Comparaison:

- JS `array.push()` ressemble à `append()`
- Python n'a pas besoin d'une syntaxe spéciale pour insérer en début : `insert(0, ...)`

### 4. Supprimer un élément avec `del`

Utilise `del` si tu veux supprimer un élément par index sans récupérer sa valeur.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
del motorcycles[1]
```

`del` est une instruction Python, pas une méthode de liste.

### 5. Supprimer et récupérer avec `pop()`

`pop()` supprime un élément et retourne sa valeur.

```python
motorcycles = ["honda", "yamaha", "suzuki"]

last_owned = motorcycles.pop()
first_owned = motorcycles.pop(0)
```

- `pop()` sans argument retire le dernier élément
- `pop(0)` retire l'élément à l'index `0`

Pont mental:

- JS : `array.pop()` retire le dernier
- Python : même idée, mais tu peux aussi retirer par index

### 6. Supprimer par valeur avec `remove()`

Si tu connais la valeur et pas sa position, utilise `remove()`.

```python
motorcycles = ["honda", "yamaha", "suzuki", "ducati"]
motorcycles.remove("ducati")
```

- supprime la première occurrence trouvée
- si la valeur n'existe pas, Python lève une erreur

Important:

- `pop()` supprime par position
- `remove()` supprime par valeur

### 7. Trier une liste

Tu as deux manières principales de trier.

```python
cars = ["bmw", "audi", "toyota", "subaru"]

cars.sort()
print(cars)
```

`sort()` modifie la liste originale.

```python
cars = ["bmw", "audi", "toyota", "subaru"]

print(sorted(cars))
print(cars)
```

`sorted()` retourne une nouvelle vue triée sans modifier la liste d'origine.

Tu peux aussi inverser l'ordre du tri :

```python
cars.sort(reverse=True)
print(sorted(cars, reverse=True))
```

### 8. Inverser l'ordre avec `reverse()`

`reverse()` ne trie pas. Il inverse juste l'ordre actuel des éléments.

```python
cars = ["bmw", "audi", "toyota", "subaru"]
cars.reverse()
```

Si la liste était déjà dans un ordre quelconque, cet ordre est simplement retourné.

### 9. Connaître la taille d'une liste

```python
cars = ["bmw", "audi", "toyota", "subaru"]
print(len(cars))
```

- Python : `len(cars)`
- JS : `cars.length`
- PHP : `count($cars)`

En Python, `len(...)` est une fonction built-in, pas une propriété.

### 10. Erreur classique : `IndexError`

Si tu demandes un index inexistant, Python lève une erreur.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
print(motorcycles[3])
```

Erreur :

```python
IndexError: list index out of range
```

Cause :

- la liste contient 3 éléments
- les index valides sont `0`, `1` et `2`

## Tableau mental à retenir

- `del liste[i]` : supprimer par index, sans récupérer
- `liste.pop()` : supprimer le dernier et récupérer
- `liste.pop(i)` : supprimer à un index et récupérer
- `liste.remove(x)` : supprimer par valeur
- `liste.sort()` : trier en place
- `sorted(liste)` : trier sans modifier l'original
- `liste.reverse()` : inverser l'ordre actuel
- `len(liste)` : obtenir la taille
- `liste[-1]` : accéder au dernier élément

## Différences utiles par rapport à JS/PHP

- Python a `remove(valeur)` directement sur les listes
- `sorted(...)` est très pratique quand tu veux garder la liste d'origine intacte
- `-1` pour le dernier élément est une habitude Python importante
- `del` est une instruction du langage, pas une méthode appelée sur la liste

## En une phrase

Le chapitre 3 t'apprend à manipuler une liste Python comme une structure simple, mutable et très pratique : lire, modifier, supprimer, trier, inverser et compter.

## Mini fiche de révision

```python
names = ["ada", "grace", "margaret"]

names[0]          # premier élément
names[-1]         # dernier élément
names.append("linus")
names.insert(1, "guido")
del names[0]
last_name = names.pop()
names.remove("grace")
names.sort()
sorted_names = sorted(names)
names.reverse()
count = len(names)
```
