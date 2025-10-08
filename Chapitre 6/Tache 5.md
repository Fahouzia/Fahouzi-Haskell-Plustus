##HC6T5 : Inverser une liste (récursif)

## Objectif

Créer une fonction `reverseList` qui **inverse une liste** (ex : `[1,2,3] → [3,2,1]`) en utilisant **la récursion**.

---

##  Code 

```haskell

-- Définition de la fonction reverseList
reverseList :: [a] -> [a]
reverseList [] = []                     -- Cas de base : une liste vide reste vide
reverseList (x:xs) = reverseList xs ++ [x]  -- Étape récursive

-- Fonction principale main pour tester
main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    let resultat = reverseList liste
    putStrLn ("La liste originale est : " ++ show liste)
    putStrLn ("La liste inversée est : " ++ show resultat)
```

---

##  Explication pas à pas

### 1. Comprendre le problème

On veut inverser une liste comme ceci :

```
[1, 2, 3, 4, 5]  →  [5, 4, 3, 2, 1]
```

---

### 2. Structure d’une fonction récursive sur une liste

Une fonction récursive sur une liste en Haskell se décompose souvent en deux parties :

```haskell
nom [] = ...         -- Cas de base (liste vide)
nom (x:xs) = ...     -- Cas récursif (tête x + reste xs)
```

---

### 3. Cas de base

```haskell
reverseList [] = []
```

 Si la liste est vide, il n’y a rien à inverser → on renvoie `[]`.

---

### 4. Cas récursif

```haskell
reverseList (x:xs) = reverseList xs ++ [x]
```

* On **inverse le reste** de la liste (`xs`) récursivement
* Puis on **ajoute l’élément courant** `x` à la **fin** du résultat.

---

### 5. Déroulement d’un exemple

Prenons la liste `[1,2,3]`.

```
reverseList [1,2,3]
→ reverseList [2,3] ++ [1]
→ (reverseList [3] ++ [2]) ++ [1]
→ ((reverseList [] ++ [3]) ++ [2]) ++ [1]
→ (([] ++ [3]) ++ [2]) ++ [1]
→ ([3] ++ [2]) ++ [1]
→ [3,2] ++ [1]
→ [3,2,1]
```

Résultat final : `[3,2,1]`

---

### 6. Fonction `main`

```haskell
main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    let resultat = reverseList liste
    putStrLn ("La liste originale est : " ++ show liste)
    putStrLn ("La liste inversée est : " ++ show resultat)
```

Cette partie permet de :

* définir une liste `[1,2,3,4,5]`
* appeler la fonction `reverseList`
* afficher les deux listes à l’écran.

---

##  Exemple de sortie

```
La liste originale est : [1,2,3,4,5]
La liste inversée est : [5,4,3,2,1]
```
