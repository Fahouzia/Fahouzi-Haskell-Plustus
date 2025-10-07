HC5T2 : Filtrer les nombres impairs

```haskell
-- Liste des entiers de 1 à 30
numbers :: [Int]
numbers = [1..30]

-- Filtrer les nombres impairs
oddNumbers :: [Int]
oddNumbers = filter odd numbers

-- Exemple d'affichage
main :: IO ()
main = print oddNumbers
```

### Explication

* `[1..30]` crée la liste `[1,2,3,...,30]`.
* `filter odd numbers` garde seulement les éléments pour lesquels `odd x` est `True` (c’est-à-dire les nombres impairs).
* Le résultat sera :

```haskell
[1,3,5,7,9,11,13,15,17,19,21,23,25,27,29]
```

---

```haskell
numbers :: [Int]
numbers = [1..30]
```

* `numbers` est une **liste d’entiers** (`[Int]`).
* `[1..30]` est une **notation Haskell** pour créer une liste allant de 1 à 30, inclusivement.
* Résultat : `[1,2,3,...,30]`.

---

```haskell
oddNumbers :: [Int]
oddNumbers = filter odd numbers
```

* `filter` est une fonction prédéfinie qui prend **une condition** (une fonction qui retourne `Bool`) et une liste.
* `odd` est une fonction prédéfinie qui renvoie `True` si un nombre est impair, `False` sinon.
* Donc `filter odd numbers` parcourt la liste `numbers` et **garde seulement les éléments pour lesquels `odd` renvoie True**.
* Résultat : `[1,3,5,7,9,11,13,15,17,19,21,23,25,27,29]`.

---

```haskell
main :: IO ()
main = print oddNumbers
```

* `main` est le point d’entrée d’un programme Haskell.
* `print oddNumbers` affiche la liste des nombres impairs à l’écran.

---
