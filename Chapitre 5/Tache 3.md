HC5T3 : Vérifier la présence de majuscules

### Étape 1 : Comprendre `any`

* `any :: (a -> Bool) -> [a] -> Bool`
* Elle retourne `True` si **au moins un élément de la liste satisfait la condition**, sinon `False`.

---

### Étape 2 : Vérifier si un mot commence par une majuscule

* On peut utiliser `isUpper` (importée depuis `Data.Char`) qui retourne `True` si un caractère est une majuscule.
* Pour vérifier le **premier caractère** d’un mot : `isUpper (head mot)`.

---

### Étape 3 : Définir la fonction
  CODE 
```haskell
import Data.Char (isUpper)

-- Vérifie si au moins un mot commence par une majuscule
hasCapital :: [String] -> Bool
hasCapital mots = any (\mot -> isUpper (head mot)) mots

-- Exemple d'utilisation
main :: IO ()
main = do
    print (hasCapital ["hello", "World", "haskell"]) -- True
    print (hasCapital ["hello", "world", "haskell"]) -- False
```

---

### Explication

1. `\mot -> isUpper (head mot)` est une **fonction lambda** qui prend un mot et renvoie `True` si la première lettre est une majuscule.
2. `any (...) mots` parcourt la liste et retourne `True` dès qu’un mot commence par une majuscule.
3. Résultat pour l’exemple :

   * `["hello", "World", "haskell"]` → `True` (car "World" commence par W)
   * `["hello", "world", "haskell"]` → `False` (aucune majuscule)

---

---

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
