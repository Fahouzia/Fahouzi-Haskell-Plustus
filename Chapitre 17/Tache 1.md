**HC17T1 : Type de données `Severity` et instance `Semigroup`**

---

###  Objectif

Créer un type de données `Severity` représentant quatre niveaux de sévérité :

* `Low`
* `Medium`
* `High`
* `Critical`

Puis définir une instance **`Semigroup`** pour pouvoir combiner deux sévérités et obtenir la plus sévère des deux.

---

###  Code

```haskell
-- HC17T1 : Type Severity et instance Semigroup

-- Définition du type de données
data Severity = Low | Medium | High | Critical
    deriving (Show, Eq, Ord)

-- Instance Semigroup : combine deux sévérités et garde la plus élevée
instance Semigroup Severity where
    s1 <> s2 = max s1 s2

-- Programme principal pour tester
main :: IO ()
main = do
    let s1 = Medium
        s2 = High
        s3 = Low
    putStrLn "=== Test du type Severity et Semigroup ==="
    putStrLn ("s1 : " ++ show s1)
    putStrLn ("s2 : " ++ show s2)
    putStrLn ("s3 : " ++ show s3)
    putStrLn ("s1 <> s2 = " ++ show (s1 <> s2))
    putStrLn ("s1 <> s3 = " ++ show (s1 <> s3))
```

---

###  Explications pas à pas

1. **Définition du type `Severity`**

```haskell
data Severity = Low | Medium | High | Critical
    deriving (Show, Eq, Ord)
```

* `Show` : permet d’afficher la valeur avec `show`.
* `Eq` : permet de comparer les valeurs avec `==`.
* `Ord` : permet de comparer l’ordre avec `<`, `>`, et `max`.

2. **Instance `Semigroup`**

```haskell
instance Semigroup Severity where
    s1 <> s2 = max s1 s2
```

* L’opérateur `<>` combine deux sévérités et retourne **la plus élevée**.
* `max` utilise l’ordre défini par `Ord`.

3. **Bloc `main`**

* Teste la combinaison de plusieurs sévérités avec `<>`.
* Affiche le résultat.

---

###  Exemple d’exécution

```
=== Test du type Severity et Semigroup ===
s1 : Medium
s2 : High
s3 : Low
s1 <> s2 = High
s1 <> s3 = Medium
```


