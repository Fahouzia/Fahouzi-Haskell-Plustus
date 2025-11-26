 **HC17T5 : Fonction `combineLists`**

---

### 🎯 Objectif

Créer une fonction `combineLists` qui utilise l’**instance `Semigroup`** des listes pour **concaténer deux listes d’entiers**.

* En Haskell, les listes sont déjà des instances de `Semigroup` et `Monoid`.
* L’opérateur `<>` correspond à la concaténation des listes.

---

### Code
```haskell
-- HC17T5 : Fonction combineLists utilisant Semigroup

import Data.Semigroup

-- Fonction qui combine deux listes d'entiers
combineLists :: [Int] -> [Int] -> [Int]
combineLists xs ys = xs <> ys  -- ou xs `mappend` ys

-- Programme principal pour tester
main :: IO ()
main = do
    let liste1 = [1,2,3]
        liste2 = [4,5,6]
    putStrLn "=== Test combineLists ==="
    putStrLn ("Liste 1 : " ++ show liste1)
    putStrLn ("Liste 2 : " ++ show liste2)
    putStrLn ("Liste combinée : " ++ show (combineLists liste1 liste2))
```

---

###  Explications pas à pas

1. **Instance Semigroup pour les listes**

```haskell
xs <> ys
```

* L’opérateur `<>` concatène deux listes.
* C’est exactement le comportement que l’on souhaite pour `combineLists`.

2. **Alternative**

```haskell
xs `mappend` ys
```

* `mappend` est équivalent à `<>` car les listes sont aussi des instances de `Monoid`.

3. **Bloc `main`**

* Déclare deux listes d’entiers.
* Combine les listes avec `combineLists`.
* Affiche le résultat.

---

### 🧩 Exemple d’exécution

```
=== Test combineLists ===
Liste 1 : [1,2,3]
Liste 2 : [4,5,6]
Liste combinée : [1,2,3,4,5,6]
```

