 HC7T1 : Implémenter Eq pour un type personnalisé

## Objectif

* Définir un **type de données `Color`** : `Red`, `Green`, `Blue`.
* Implémenter **`Eq`** pour que deux couleurs du **même type soient égales**.

---

##  Code 

```haskell
--
-- Définition du type Color
data Color = Red | Green | Blue

-- Implémentation de la classe Eq
instance Eq Color where
    Red   == Red   = True
    Green == Green = True
    Blue  == Blue  = True
    _     == _     = False  -- Toutes les autres combinaisons → False

-- Fonction principale main pour tester
main :: IO ()
main = do
    let c1 = Red
    let c2 = Green
    let c3 = Red

    putStrLn ("Red == Green ? " ++ show (c1 == c2))
    putStrLn ("Red == Red ? " ++ show (c1 == c3))
    putStrLn ("Green == Blue ? " ++ show (c2 == Blue))
```

---

##  Explication pas à pas

### 1️ Définition du type

```haskell
data Color = Red | Green | Blue
```

* `data` → permet de créer un **type personnalisé**
* `Color` a **3 valeurs possibles** : `Red`, `Green`, `Blue`

---

### 2️ Implémentation de `Eq`

```haskell
instance Eq Color where
    Red   == Red   = True
    Green == Green = True
    Blue  == Blue  = True
    _     == _     = False
```

* `instance Eq Color` → dit à Haskell comment comparer les couleurs
* Pour chaque couleur égale à elle-même → `True`
* Toutes les autres combinaisons (`Red == Green`, etc.) → `False`
* `_` → symbole **joker**, correspond à n’importe quelle valeur

---

### 3️ Fonction `main` (tests)

```haskell
main :: IO ()
main = do
    let c1 = Red
    let c2 = Green
    let c3 = Red

    putStrLn ("Red == Green ? " ++ show (c1 == c2))
    putStrLn ("Red == Red ? " ++ show (c1 == c3))
    putStrLn ("Green == Blue ? " ++ show (c2 == Blue))
```

* `show` convertit le résultat `Bool` en chaîne lisible
* On teste **Red vs Green**, **Red vs Red**, **Green vs Blue**

---

###  Exemple de sortie

```
Red == Green ? False
Red == Red ? True
Green == Blue ? False
```

---
