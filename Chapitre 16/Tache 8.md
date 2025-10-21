 **HC16T8 : Tri par insertion**
---

###  Objectif

Créer une fonction qui trie une **liste d’entiers** en utilisant l’**algorithme de tri par insertion**.

**Principe du tri par insertion** :

1. On commence avec une liste vide triée.
2. On parcourt les éléments de la liste à trier.
3. On insère chaque élément à sa place dans la liste triée.

---

### Code

```haskell
-- HC16T8 : Tri par insertion

-- Fonction qui insère un élément dans une liste triée
inserer :: Int -> [Int] -> [Int]
inserer x [] = [x]
inserer x (y:ys)
    | x <= y    = x : y : ys
    | otherwise = y : inserer x ys

-- Fonction de tri par insertion
insertionSort :: [Int] -> [Int]
insertionSort [] = []
insertionSort (x:xs) = inserer x (insertionSort xs)

-- Programme principal pour tester
main :: IO ()
main = do
    putStrLn "=== Tri par insertion ==="
    putStrLn "Entrez une liste de nombres séparés par des espaces :"
    input <- getLine
    let liste = map read (words input) :: [Int]
    let sorted = insertionSort liste
    putStrLn ("Liste triée : " ++ show sorted)
```

---

###  Explications pas à pas

1. **Fonction `inserer`**

```haskell
inserer x [] = [x]
inserer x (y:ys)
    | x <= y    = x : y : ys
    | otherwise = y : inserer x ys
```

* Insère `x` dans une liste déjà triée `(y:ys)` à la bonne position.
* Cas de base : liste vide → `[x]`.
* Sinon, on compare `x` avec le premier élément `y` :

  * Si `x <= y`, `x` vient avant `y`.
  * Sinon, on continue à insérer dans le reste de la liste `ys`.

2. **Fonction `insertionSort`**

```haskell
insertionSort [] = []
insertionSort (x:xs) = inserer x (insertionSort xs)
```

* Tri récursif :

  * On trie le reste de la liste `xs`.
  * On insère la tête `x` dans la liste triée.

3. **Bloc `main`**

* Lit une liste d’entiers de l’utilisateur.
* Trie la liste avec `insertionSort`.
* Affiche la liste triée.

---

### 🧩 Exemple d’exécution

```
=== Tri par insertion ===
Entrez une liste de nombres séparés par des espaces :
5 2 8 1 4
Liste triée : [1,2,4,5,8]
```

