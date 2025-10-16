HC11T7 : Instance Ord pour Box


### 🔹 Énoncé

> Implémenter l’instance `Ord` pour le type `Box` en utilisant la fonction `compare`.

---

###  Code 

```haskell
-- Définition du type Box
data Box a = Empty | Has a
  deriving (Show, Eq)

-- Implémentation de l'instance Ord
instance (Ord a) => Ord (Box a) where
  compare Empty Empty = EQ                  -- Deux boîtes vides sont égales
  compare Empty (Has _) = LT                -- Une boîte vide est plus petite qu'une boîte pleine
  compare (Has _) Empty = GT                -- Une boîte pleine est plus grande qu'une boîte vide
  compare (Has x) (Has y) = compare x y     -- Sinon, on compare les valeurs contenues

-- Fonction main pour tester
main :: IO ()
main = do
  let b1 = Has 10
  let b2 = Has 20
  let b3 = Empty
  let b4 = Has 10

  putStrLn ("Comparaison b1 et b2 : " ++ show (compare b1 b2))   -- LT car 10 < 20
  putStrLn ("Comparaison b2 et b1 : " ++ show (compare b2 b1))   -- GT car 20 > 10
  putStrLn ("Comparaison b1 et b4 : " ++ show (compare b1 b4))   -- EQ car 10 == 10
  putStrLn ("Comparaison b3 et b1 : " ++ show (compare b3 b1))   -- LT car Empty < Has
  putStrLn ("Comparaison b1 et b3 : " ++ show (compare b1 b3))   -- GT car Has > Empty
```

---

### 🔹 Explication pas à pas

1. **Définition du type `Box` :**

   ```haskell
   data Box a = Empty | Has a
   ```

   → Une boîte peut être vide (`Empty`) ou contenir une valeur (`Has a`).

2. **Instance `Ord` :**
   On définit comment comparer deux `Box`.

   * `compare Empty Empty = EQ`
     Deux boîtes vides sont égales.

   * `compare Empty (Has _) = LT`
     Une boîte vide est considérée **plus petite** qu’une boîte pleine.

   * `compare (Has _) Empty = GT`
     Une boîte pleine est **plus grande** qu’une boîte vide.

   * `compare (Has x) (Has y) = compare x y`
     Si les deux boîtes contiennent des valeurs, on compare directement ces valeurs à l’aide de `compare`.

3. **Test dans `main` :**
   On crée plusieurs boîtes (`b1`, `b2`, `b3`, `b4`) et on compare leurs contenus.

---

### 🔹 Exemple de sortie

```
Comparaison b1 et b2 : LT
Comparaison b2 et b1 : GT
Comparaison b1 et b4 : EQ
Comparaison b3 et b1 : LT
Comparaison b1 et b3 : GT
```

---
