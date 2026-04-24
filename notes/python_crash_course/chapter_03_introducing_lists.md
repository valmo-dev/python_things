### Python Crash Course: Chapter 3 - Introducing Lists

## Resume

Une `list` Python est l'equivalent d'un tableau JavaScript ou d'un array indexe PHP.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
```

Dans ce chapitre, l'idee principale est d'apprendre a manipuler une liste proprement:

1. acceder aux elements
2. ajouter ou supprimer des elements
3. trier ou inverser une liste
4. connaitre sa taille
5. eviter les erreurs d'index

## Les points importants

### 1. Indexation

Python commence a l'index `0`, comme JavaScript.

```python
motorcycles = ["honda", "yamaha", "suzuki"]

print(motorcycles[0])
print(motorcycles[1])
print(motorcycles[-1])
```

- `motorcycles[0]` : premier element
- `motorcycles[-1]` : dernier element
- l'index negatif est tres idiomatique en Python

Pont mental JS/PHP:

- JS : `motorcycles[0]`
- PHP : `$motorcycles[0]`
- Python : meme idee, mais `-1` pour le dernier element est beaucoup plus courant

### 2. Modifier un element

Une liste est mutable. Tu peux remplacer une valeur a une position donnee.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
motorcycles[0] = "ducati"
```

Comme en JS, tu modifies le contenu existant au lieu de recreer toute la structure.

### 3. Ajouter des elements

```python
motorcycles = ["honda", "yamaha", "suzuki"]

motorcycles.append("ducati")
motorcycles.insert(0, "bmw")
```

- `append()` ajoute a la fin
- `insert(index, valeur)` insere a une position precise

Comparaison:

- JS `array.push()` ressemble a `append()`
- Python n'a pas besoin d'une syntaxe speciale pour inserer en debut: `insert(0, ...)`

### 4. Supprimer un element avec `del`

Utilise `del` si tu veux supprimer un element par index sans recuperer sa valeur.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
del motorcycles[1]
```

`del` est une instruction Python, pas une methode de liste.

### 5. Supprimer et recuperer avec `pop()`

`pop()` supprime un element et retourne sa valeur.

```python
motorcycles = ["honda", "yamaha", "suzuki"]

last_owned = motorcycles.pop()
first_owned = motorcycles.pop(0)
```

- `pop()` sans argument retire le dernier element
- `pop(0)` retire l'element a l'index `0`

Pont mental:

- JS : `array.pop()` retire le dernier
- Python : meme idee, mais tu peux aussi retirer par index

### 6. Supprimer par valeur avec `remove()`

Si tu connais la valeur et pas sa position, utilise `remove()`.

```python
motorcycles = ["honda", "yamaha", "suzuki", "ducati"]
motorcycles.remove("ducati")
```

- supprime la premiere occurrence trouvee
- si la valeur n'existe pas, Python leve une erreur

Important:

- `pop()` supprime par position
- `remove()` supprime par valeur

### 7. Trier une liste

Tu as deux manieres principales de trier.

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

`sorted()` retourne une nouvelle vue triee sans modifier la liste d'origine.

Tu peux aussi inverser l'ordre du tri:

```python
cars.sort(reverse=True)
print(sorted(cars, reverse=True))
```

### 8. Inverser l'ordre avec `reverse()`

`reverse()` ne trie pas. Il inverse juste l'ordre actuel des elements.

```python
cars = ["bmw", "audi", "toyota", "subaru"]
cars.reverse()
```

Si la liste etait deja dans un ordre quelconque, cet ordre est simplement retourne.

### 9. Connaitre la taille d'une liste

```python
cars = ["bmw", "audi", "toyota", "subaru"]
print(len(cars))
```

- Python : `len(cars)`
- JS : `cars.length`
- PHP : `count($cars)`

En Python, `len(...)` est une fonction built-in, pas une propriete.

### 10. Erreur classique: `IndexError`

Si tu demandes un index inexistant, Python leve une erreur.

```python
motorcycles = ["honda", "yamaha", "suzuki"]
print(motorcycles[3])
```

Erreur:

```python
IndexError: list index out of range
```

Cause:

- la liste contient 3 elements
- les index valides sont `0`, `1` et `2`

## Tableau mental a retenir

- `del liste[i]` : supprimer par index, sans recuperer
- `liste.pop()` : supprimer le dernier et recuperer
- `liste.pop(i)` : supprimer a un index et recuperer
- `liste.remove(x)` : supprimer par valeur
- `liste.sort()` : trier en place
- `sorted(liste)` : trier sans modifier l'original
- `liste.reverse()` : inverser l'ordre actuel
- `len(liste)` : obtenir la taille
- `liste[-1]` : acceder au dernier element

## Differences utiles par rapport a JS/PHP

- Python a `remove(valeur)` directement sur les listes
- `sorted(...)` est tres pratique quand tu veux garder la liste d'origine intacte
- `-1` pour le dernier element est une habitude Python importante
- `del` est une instruction du langage, pas une methode appelee sur la liste

## En une phrase

Le chapitre 3 t'apprend a manipuler une liste Python comme une structure simple, mutable et tres pratique: lire, modifier, supprimer, trier, inverser et compter.

## Mini fiche de revision

```python
names = ["ada", "grace", "margaret"]

names[0]          # premier element
names[-1]         # dernier element
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
