**C17T2 : Nouveaux types `Min` et `Max` avec `Semigroup`**

---

### Objectif

Créer deux types génériques pour tout type `Ord` :

1. `Min a` : combine deux valeurs et retourne la **plus petite** (`min`) avec `Semigroup`.
2. `Max a` : combine deux valeurs et retourne la **plus grande** (`max`) avec `Semigroup`.

Ces types sont utiles pour combiner des valeurs tout en conservant le minimum ou le maximum.

---

###  Code 

```haskell
-- C17T2 : Types Min et Max avec Semigroup

-- Type Min
newtype Min a = Min { getMin :: a } deriving (Show, Eq, Ord)

instance Ord a => Semigroup (Min a) where
    Min x <> Min y = Min (min x y)

-- Type Max
newtype Max a = Max { getMax :: a } deriving (Show, Eq, Ord)

instance Ord a => Semigroup (Max a) where
    Max x <> Max y = Max (max x y)

-- Programme principal pour tester
main :: IO ()
main = do
    let a = Min 10
        b = Min 5
        c = Max 10
        d = Max 15
    putStrLn "=== Test Min et Max avec Semigroup ==="
    putStrLn ("a <> b = " ++ show (a <> b)) -- Min 5
    putStrLn ("c <> d = " ++ show (c <> d)) -- Max 15
```

---

###  Explications pas à pas

1. **Définition des types `Min` et `Max`**

```haskell
newtype Min a = Min { getMin :: a } deriving (Show, Eq, Ord)
newtype Max a = Max { getMax :: a } deriving (Show, Eq, Ord)
```

* `newtype` crée un **wrapper léger** autour de `a`.
* `deriving (Show, Eq, Ord)` permet de comparer et afficher les valeurs.

2. **Instance Semigroup pour `Min`**

```haskell
instance Ord a => Semigroup (Min a) where
    Min x <> Min y = Min (min x y)
```

* Combine deux valeurs et retourne **la plus petite**.

3. **Instance Semigroup pour `Max`**

```haskell
instance Ord a => Semigroup (Max a) where
    Max x <> Max y = Max (max x y)
```

* Combine deux valeurs et retourne **la plus grande**.

4. **Bloc `main`**

* Teste la combinaison de valeurs avec `<>` et affiche les résultats.

---

### Exemple d’exécution

```
=== Test Min et Max avec Semigroup ===
a <> b = Min 5
c <> d = Max 15
```
