**HC17T7 : Fonction `multiplyProducts`**

---

###  Objectif

Créer une fonction `multiplyProducts` qui :

* Prend une **liste de valeurs `Product`**.
* Combine toutes les valeurs en utilisant **`mconcat`**.
* Retourne le **produit combiné**.

> Ici, on définit un type `Product` avec un **Monoid** où la valeur neutre est `1` et la combinaison est la multiplication.

---

###  Code 

```haskell
-- HC17T7 : Fonction multiplyProducts

import Data.Monoid

-- Définition du type Product
newtype Product a = Product { getProduct :: a } deriving (Show, Eq)

-- Semigroup : multiplication
instance Num a => Semigroup (Product a) where
    Product x <> Product y = Product (x * y)

-- Monoid : élément neutre = 1
instance Num a => Monoid (Product a) where
    mempty = Product 1
    mappend = (<>)

-- Fonction qui multiplie une liste de Product
multiplyProducts :: Num a => [Product a] -> Product a
multiplyProducts = mconcat

-- Programme principal pour tester
main :: IO ()
main = do
    let valeurs = [Product 2, Product 3, Product 4]
    putStrLn "=== Test multiplyProducts ==="
    putStrLn ("Liste de valeurs : " ++ show (map getProduct valeurs))
    putStrLn ("Produit total : " ++ show (getProduct (multiplyProducts valeurs)))
```

---

### 🔍 Explications pas à pas

1. **Définition du type `Product`**

```haskell
newtype Product a = Product { getProduct :: a } deriving (Show, Eq)
```

* `newtype` crée un wrapper léger autour de `a`.
* `getProduct` permet de récupérer la valeur.

2. **Instance `Semigroup`**

```haskell
Product x <> Product y = Product (x * y)
```

* `<>` multiplie deux valeurs `Product`.

3. **Instance `Monoid`**

```haskell
mempty = Product 1
mappend = (<>)
```

* `mempty` est l’élément neutre (`1`).
* Permet d’utiliser `mconcat` pour combiner toute une liste.

4. **Fonction `multiplyProducts`**

```haskell
multiplyProducts = mconcat
```

* `mconcat` combine tous les éléments de la liste en utilisant `mappend` (ici multiplication).

5. **Bloc `main`**

* Teste la fonction avec une liste de `Product`.
* Affiche le résultat.

---

### 🧩 Exemple d’exécution

```
=== Test multiplyProducts ===
Liste de valeurs : [2,3,4]
Produit total : 24
```

---

Si tu veux, je peux te montrer **une version générique** qui fonctionne avec **n’importe quel type `Num`** et permet de combiner des listes mixtes de produits.
Veux‑tu que je fasse ça ?
