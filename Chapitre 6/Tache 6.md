HC6T6 : Existence d'un élément dans une liste

## Objectif

Créer une fonction `elementExists` qui prend :

* un **élément** `e`
* une **liste** `lst`

et retourne **True** si l’élément existe dans la liste, **False** sinon.

---

##  Code 

```haskell
-- 
-- Définition de la fonction elementExists
elementExists :: Eq a => a -> [a] -> Bool
elementExists _ [] = False                  -- Cas de base : liste vide → élément non trouvé
elementExists e (x:xs)
    | e == x    = True                      -- Si l'élément courant est égal à e → True
    | otherwise = elementExists e xs        -- Sinon, on cherche dans le reste de la liste

-- Fonction principale main pour tester
main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    putStrLn ("Liste : " ++ show liste)
    
    -- Test pour un élément existant
    let test1 = 3
    putStrLn ("L'élément " ++ show test1 ++ " existe ? " ++ show (elementExists test1 liste))
    
    -- Test pour un élément non existant
    let test2 = 7
    putStrLn ("L'élément " ++ show test2 ++ " existe ? " ++ show (elementExists test2 liste))
```

---

##  Explication pas à pas

### 1. Signature de la fonction

```haskell
elementExists :: Eq a => a -> [a] -> Bool
```

* `Eq a =>` : le type `a` doit être **comparables** (`==` est défini)
* `a` : l’élément à chercher
* `[a]` : la liste
* `Bool` : True ou False selon que l’élément existe ou non

---

### 2. Cas de base

```haskell
elementExists _ [] = False
```

* Si la liste est vide, l’élément **n’existe pas** → retour False.

---

### 3. Cas récursif avec gardes

```haskell
elementExists e (x:xs)
    | e == x    = True
    | otherwise = elementExists e xs
```

* `(x:xs)` : tête `x` et reste de la liste `xs`
* Si `x` est **l’élément recherché**, on renvoie `True`
* Sinon, on cherche récursivement dans `xs`

---

### 4. Exemple de déroulement

Cherchons `3` dans `[1,2,3,4,5]` :

```
elementExists 3 [1,2,3,4,5]
→ 1 == 3 ? Non → elementExists 3 [2,3,4,5]
→ 2 == 3 ? Non → elementExists 3 [3,4,5]
→ 3 == 3 ? Oui → True
```

Cherchons `7` dans `[1,2,3,4,5]` :

```
elementExists 7 [1,2,3,4,5]
→ 1 == 7 ? Non → elementExists 7 [2,3,4,5]
→ 2 == 7 ? Non → elementExists 7 [3,4,5]
→ 3 == 7 ? Non → elementExists 7 [4,5]
→ 4 == 7 ? Non → elementExists 7 [5]
→ 5 == 7 ? Non → elementExists 7 []
→ [] → False
```

---

### 5. Fonction `main`

* On teste **un élément existant** (3)
* On teste **un élément non existant** (7)
* On affiche le résultat avec `putStrLn`

---

###  Exemple de sortie

```
Liste : [1,2,3,4,5]
L'élément 3 existe ? True
L'élément 7 existe ? False
```

---

