**HC17T8 : Fonction `foldWithSemigroup`**

---

###  Objectif

Créer une fonction `foldWithSemigroup` qui :

* Prend une **liste de n’importe quel type `a`** ayant une instance `Semigroup`.
* Combine tous les éléments avec **`foldr`** et l’opérateur `<>`.
* Retourne le résultat combiné.

> Cela fonctionne pour **tous les types** qui ont un `Semigroup`, par exemple `Sum Int`, `Product Int`, `[a]`, `Severity`, etc.

---

### Code

```haskell
-- HC17T8 : Fonction foldWithSemigroup

import Data.Semigroup

-- Fonction qui combine tous les éléments d'une liste avec foldr
foldWithSemigroup :: Semigroup a => [a] -> a
foldWithSemigroup []     = error "La liste est vide"
foldWithSemigroup (x:xs) = foldr (<>) x xs

-- Programme principal pour tester
main :: IO ()
main = do
    -- Exemple avec Sum
    let valeursSum = [Sum 3, Sum 5, Sum 2]
    putStrLn "=== Test foldWithSemigroup avec Sum ==="
    putStrLn ("Liste : " ++ show (map getSum valeursSum))
    putStrLn ("Somme totale : " ++ show (getSum (foldWithSemigroup valeursSum)))

    -- Exemple avec Product
    let valeursProd = [Product 2, Product 3, Product 4]
    putStrLn "\n=== Test foldWithSemigroup avec Product ==="
    putStrLn ("Liste : " ++ show (map getProduct valeursProd))
    putStrLn ("Produit total : " ++ show (getProduct (foldWithSemigroup valeursProd)))
```

---

###  Explications pas à pas

1. **Signature de la fonction**

```haskell
foldWithSemigroup :: Semigroup a => [a] -> a
```

* La fonction accepte une **liste de n’importe quel type `a`** ayant une instance `Semigroup`.

2. **Implémentation**

```haskell
foldWithSemigroup []     = error "La liste est vide"
foldWithSemigroup (x:xs) = foldr (<>) x xs
```

* `foldr (<>) x xs` : combine tous les éléments de la liste en utilisant l’opérateur `<>`.
* On utilise le **premier élément `x` comme valeur initiale** pour éviter de dépendre d’un `Monoid`.

3. **Exemples**

* Avec `Sum` : additionne tous les éléments.
* Avec `Product` : multiplie tous les éléments.

---

###  Exemple d’exécution

```
=== Test foldWithSemigroup avec Sum ===
Liste : [3,5,2]
Somme totale : 10

=== Test foldWithSemigroup avec Product ===
Liste : [2,3,4]
Produit total : 24
```

