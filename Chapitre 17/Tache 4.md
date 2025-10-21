**HC17T4 : Instance `Monoid` pour `Sum`**

---

###  Objectif

Créer un **nouveau type `Sum`** pour encapsuler des nombres et définir une instance `Monoid` :

* L’élément neutre (`mempty`) doit être `0`.
* La combinaison (`mappend` ou `<>`) doit correspondre à l’**addition** des valeurs.
* Permet d’utiliser `mconcat` pour additionner facilement plusieurs valeurs.

---

###Code 

```haskell
-- HC17T4 : Instance Monoid pour Sum

import Data.Semigroup

-- Définition du type Sum
newtype Sum a = Sum { getSum :: a } deriving (Show, Eq)

-- Semigroup pour Sum : addition
instance Num a => Semigroup (Sum a) where
    Sum x <> Sum y = Sum (x + y)

-- Monoid pour Sum : élément neutre = 0
instance Num a => Monoid (Sum a) where
    mempty = Sum 0
    mappend = (<>)

-- Programme principal pour tester
main :: IO ()
main = do
    let valeurs = [Sum 3, Sum 5, Sum 2]
    putStrLn "=== Test Monoid Sum ==="
    putStrLn ("Liste de valeurs : " ++ show (map getSum valeurs))
    putStrLn ("Somme totale : " ++ show (getSum (mconcat valeurs)))
```

---

### 🔍 Explications pas à pas

1. **Définition du type `Sum`**

```haskell
newtype Sum a = Sum { getSum :: a } deriving (Show, Eq)
```

* `newtype` crée un wrapper léger autour de `a`.
* `getSum` permet de récupérer la valeur encapsulée.

2. **Instance `Semigroup`**

```haskell
instance Num a => Semigroup (Sum a) where
    Sum x <> Sum y = Sum (x + y)
```

* `<>` additionne deux valeurs `Sum`.

3. **Instance `Monoid`**

```haskell
instance Num a => Monoid (Sum a) where
    mempty = Sum 0
    mappend = (<>)
```

* `mempty` est l’élément neutre (`0`).
* `mappend` utilise l’addition définie par `Semigroup`.

4. **Bloc `main`**

* Déclare une liste de `Sum`.
* Utilise `mconcat` pour obtenir la somme totale.
* Affiche le résultat.

---

### 🧩 Exemple d’exécution

```
=== Test Monoid Sum ===
Liste de valeurs : [3,5,2]
Somme totale : 10
```


