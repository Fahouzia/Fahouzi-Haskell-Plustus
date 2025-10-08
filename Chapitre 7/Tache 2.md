HC7T2 : Implémenter Ord pour Color


## Objectif

* Utiliser le type `Color` défini précédemment (`Red`, `Green`, `Blue`)
* Implémenter **`Ord`** pour que l’ordre soit :

```
Red < Green < Blue
```

---

##  Code 
```haskell
-- HC7T2 : Implémenter Ord pour Color

-- Type Color (déjà défini)
data Color = Red | Green | Blue
    deriving (Eq, Show)  -- On dérive Eq et Show pour faciliter les comparaisons et l'affichage

-- Implémentation de la classe Ord
instance Ord Color where
    compare Red Red     = EQ
    compare Red _       = LT
    compare Green Red   = GT
    compare Green Green = EQ
    compare Green Blue  = LT
    compare Blue Blue   = EQ
    compare Blue _      = GT

-- Fonction principale main pour tester
main :: IO ()
main = do
    let c1 = Red
    let c2 = Green
    let c3 = Blue

    putStrLn ("Red < Green ? " ++ show (c1 < c2))
    putStrLn ("Green < Blue ? " ++ show (c2 < c3))
    putStrLn ("Blue > Red ? " ++ show (c3 > c1))
    putStrLn ("Green == Green ? " ++ show (c2 == Green))
```

---

##  Explication pas à pas

### 1️⃣ Définition du type

```haskell
data Color = Red | Green | Blue
    deriving (Eq, Show)
```

* `deriving Eq` → on peut utiliser `==` et `/=`
* `deriving Show` → on peut afficher facilement les couleurs

---

### 2️⃣ Implémentation de `Ord`

```haskell
instance Ord Color where
    compare Red Red     = EQ
    compare Red _       = LT
    compare Green Red   = GT
    compare Green Green = EQ
    compare Green Blue  = LT
    compare Blue Blue   = EQ
    compare Blue _      = GT
```

* `compare a b` renvoie :

  * `LT` si `a < b`
  * `GT` si `a > b`
  * `EQ` si `a == b`

* On définit explicitement **l’ordre souhaité** : `Red < Green < Blue`

* `_` → joker pour toutes les autres valeurs

---

### 3️⃣ Fonction `main` (tests)

```haskell
main :: IO ()
main = do
    let c1 = Red
    let c2 = Green
    let c3 = Blue

    putStrLn ("Red < Green ? " ++ show (c1 < c2))
    putStrLn ("Green < Blue ? " ++ show (c2 < c3))
    putStrLn ("Blue > Red ? " ++ show (c3 > c1))
    putStrLn ("Green == Green ? " ++ show (c2 == Green))
```

* Tests des relations `<`, `>`, `==`
* `show` convertit `Bool` en texte lisible

---

###  Exemple de sortie

```
Red < Green ? True
Green < Blue ? True
Blue > Red ? True
Green == Green ? True
```

