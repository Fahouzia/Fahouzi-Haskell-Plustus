##  HC6T7 : Taille d'une liste

##  Objectif

Créer une fonction `listLength` qui prend une **liste** et retourne le **nombre d’éléments** qu’elle contient.

---

##  Code 

```haskell
--

-- Définition de la fonction listLength (récursive)
listLength :: [a] -> Int
listLength [] = 0                   -- Cas de base : liste vide → longueur 0
listLength (_:xs) = 1 + listLength xs   -- On compte 1 pour la tête + longueur du reste

-- Fonction principale main pour tester
main :: IO ()
main = do
    let liste1 = [1, 2, 3, 4, 5]
    let liste2 = ["a", "b", "c"]
    
    putStrLn ("Liste 1 : " ++ show liste1 ++ " → longueur : " ++ show (listLength liste1))
    putStrLn ("Liste 2 : " ++ show liste2 ++ " → longueur : " ++ show (listLength liste2))
```

---

##  Explication pas à pas

### 1. Signature de la fonction

```haskell
listLength :: [a] -> Int
```

* `[a]` : liste de n’importe quel type
* `Int` : longueur de la liste
* La fonction est **générique** (peut prendre `[Int]`, `[Char]`, `[String]`, etc.)

---

### 2. Cas de base

```haskell
listLength [] = 0
```

* Si la liste est vide, sa longueur est **0**.

---

### 3. Cas récursif

```haskell
listLength (_:xs) = 1 + listLength xs
```

* `(_:xs)` : ignore la tête (`_`) et prend le reste de la liste `xs`
* On ajoute `1` (pour la tête) à la longueur du reste
* La fonction **s’appelle récursivement** jusqu’à la liste vide

---

### 4. Exemple de déroulement

Pour `[1,2,3]` :

```
listLength [1,2,3]
→ 1 + listLength [2,3]
→ 1 + (1 + listLength [3])
→ 1 + (1 + (1 + listLength []))
→ 1 + (1 + (1 + 0))
→ 3
```

---

### 5. Fonction `main`

* Test avec `[1,2,3,4,5]` → longueur 5
* Test avec `["a","b","c"]` → longueur 3
* Affichage avec `putStrLn` et `show`

---

###  Exemple de sortie

```
Liste 1 : [1,2,3,4,5] → longueur : 5
Liste 2 : ["a","b","c"] → longueur : 3
```

---

Veux‑tu que je fasse ça ?
