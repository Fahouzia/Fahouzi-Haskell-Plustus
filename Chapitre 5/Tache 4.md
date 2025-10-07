HC5T4 : Utiliser les fonctions lambda

code :
```haskell
import Data.Char (isUpper)

-- Fonction qui vérifie si au moins un mot commence par une majuscule
hasCapital :: [String] -> Bool
hasCapital mots = any (\mot -> not (null mot) && isUpper (head mot)) mots

-- Exemple d'utilisation
main :: IO ()
main = do
    print (hasCapital ["hello", "World", "haskell"])  -- True
    print (hasCapital ["hello", "world", "haskell"])  -- False
    print (hasCapital ["", "bonjour", "Paris"])       -- True
```

---

### Explication rapide :

* `not (null mot)` vérifie que le mot n’est **pas vide** (évite une erreur avec `head mot`).
* `isUpper (head mot)` vérifie si la **première lettre** est une majuscule.
* `any` retourne `True` dès qu’un mot correspond à cette condition.



```haskell
import Data.Char (isUpper)
```

* On importe `isUpper` depuis le module `Data.Char`.
* `isUpper :: Char -> Bool` retourne `True` si le caractère est une **majuscule**, sinon `False`.

---

```haskell
hasCapital :: [String] -> Bool
```

* `hasCapital` est le **nom de la fonction**.
* Type `[String] -> Bool` : elle prend **une liste de mots** (chaînes de caractères) et retourne `True` ou `False`.

---

```haskell
hasCapital mots = any (\mot -> isUpper (head mot)) mots
```

* `any :: (a -> Bool) -> [a] -> Bool` : retourne `True` si **au moins un élément** de la liste satisfait la condition.
* `\mot -> isUpper (head mot)` est une **fonction lambda** :

  1. `mot` est un mot de la liste.
  2. `head mot` récupère **la première lettre** du mot.
  3. `isUpper (head mot)` vérifie si cette lettre est une **majuscule**.
* `any (\mot -> isUpper (head mot)) mots` : parcourt tous les mots et renvoie `True` dès qu’il trouve un mot qui commence par une majuscule.

---

```haskell
main :: IO ()
main = do
    print (hasCapital ["hello", "World", "haskell"]) -- True
    print (hasCapital ["hello", "world", "haskell"]) -- False
```

* `main` sert à **tester la fonction**.
* Premier exemple : `"World"` commence par une majuscule → `True`.
* Deuxième exemple : aucun mot ne commence par une majuscule → `False`.

---


La fonction `hasCapital` vérifie simplement s’il y a **au moins un mot qui commence par une majuscule** dans une liste.

* `any` : test “au moins un vrai”.
* `head` : première lettre.
* `isUpper` : majuscule.

---
