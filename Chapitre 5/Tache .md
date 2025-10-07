HC5T5 : Application partielle

CODE

```haskell
(*) :: Num a => a -> a -> a
```

Donc `(*) 5` est une **fonction partielle** qui multiplie son argument par 5.

---

### Code complet

```haskell
-- Définition de la fonction multiplyByFive avec application partielle
multiplyByFive :: Int -> Int
multiplyByFive = (5 *)

-- Exemple d'utilisation
main :: IO ()
main = do
    print (multiplyByFive 3)   -- 15
    print (multiplyByFive 10)  -- 50
    print (multiplyByFive (-2)) -- -10
```

---

### Explication ligne par ligne

1. `multiplyByFive :: Int -> Int`
   → La fonction prend un entier et retourne un entier.

2. `multiplyByFive = (5 *)`
   → On ne met **qu’un seul argument** à l’opérateur `*`.
   → `(5 *)` signifie « une fonction qui multiplie son argument par 5 ».

3. Dans `main`, on teste la fonction :

   * `multiplyByFive 3` → `15`
   * `multiplyByFive 10` → `50`
   * `multiplyByFive (-2)` → `-10`

---
