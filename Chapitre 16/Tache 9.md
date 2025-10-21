**HC16T9 : Supprimer les doublons d’une liste** 

---

### Objectif

Créer une fonction qui prend une **liste** et retourne une nouvelle liste 
**sans doublons**, en conservant l’ordre des premiers éléments rencontrés.

Exemple :

* `[1,2,3,2,4,1]` → `[1,2,3,4]`
* `"abbaca"` → `"abca"`

---

###  Code

```haskell
-- HC16T9 : Supprimer les doublons d'une liste

-- Fonction qui supprime les doublons
supprimerDoublons :: Eq a => [a] -> [a]
supprimerDoublons [] = []
supprimerDoublons (x:xs)
    | x `elem` xs = supprimerDoublons xs
    | otherwise   = x : supprimerDoublons xs

-- Version alternative qui conserve le premier élément rencontré
supprimerDoublonsPreserve :: Eq a => [a] -> [a]
supprimerDoublonsPreserve [] = []
supprimerDoublonsPreserve (x:xs)
    | x `elem` xs = x : supprimerDoublonsPreserve (filter (/= x) xs)
    | otherwise   = x : supprimerDoublonsPreserve xs

-- Programme principal pour tester
main :: IO ()
main = do
    putStrLn "=== Suppression des doublons ==="
    putStrLn "Entrez une liste d'entiers séparés par des espaces :"
    input <- getLine
    let liste = map read (words input) :: [Int]
    let unique = supprimerDoublonsPreserve liste
    putStrLn ("Liste sans doublons : " ++ show unique)
```

---

### 🔍 Explications pas à pas

1. **Signature de la fonction**

```haskell
supprimerDoublonsPreserve :: Eq a => [a] -> [a]
```

* `Eq a` : les éléments doivent être comparables avec `==`.
* La fonction prend une liste `[a]` et retourne `[a]` sans doublons.

2. **Principe**

* On parcourt la liste élément par élément.
* On utilise `filter (/= x)` pour retirer les occurrences suivantes de `x`.
* On ajoute `x` à la liste résultat uniquement **une fois**.

3. **Bloc `main`**

* Lit une liste d’entiers de l’utilisateur.
* Supprime les doublons avec `supprimerDoublonsPreserve`.
* Affiche le résultat.

---

### 🧩 Exemple d’exécution

```
=== Suppression des doublons ===
Entrez une liste d'entiers séparés par des espaces :
1 2 3 2 4 1
Liste sans doublons : [1,2,3,4]
```
se ça ?
