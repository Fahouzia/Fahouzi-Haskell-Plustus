HC6T9 : Implémentation de map

##  Objectif

Créer une fonction `myMap` qui prend :

* une **fonction** `f`
* une **liste** `[a]`

et retourne **une nouvelle liste** où **`f` a été appliquée à chaque élément** (comme le `map` standard de Haskell).

---

##  Code 

```haskell
-- 
-- Définition de la fonction myMap
myMap :: (a -> b) -> [a] -> [b]
myMap _ [] = []                     -- Cas de base : liste vide → renvoie liste vide
myMap f (x:xs) = f x : myMap f xs  -- Applique f à x, puis récursion sur le reste

-- Fonction principale main pour tester
main :: IO ()
main = do
    let liste = [1,2,3,4,5]
    
    -- Exemple : doubler chaque élément
    let resultat = myMap (\x -> x * 2) liste
    
    putStrLn ("Liste originale : " ++ show liste)
    putStrLn ("Liste après application de myMap (x*2) : " ++ show resultat)
```

---

##  Explication pas à pas

### 1️ Signature de la fonction

```haskell
myMap :: (a -> b) -> [a] -> [b]
```

* `(a -> b)` : `f` est une fonction qui prend un élément de type `a` et renvoie un élément de type `b`
* `[a]` : liste d’entrée
* `[b]` : liste de sortie après application de `f` à chaque élément

---

### 2️ Cas de base

```haskell
myMap _ [] = []
```

* Si la liste est vide → il n’y a rien à transformer → on renvoie `[]`
* `_` → indique qu’on **ignore la fonction**, car elle n’est pas utilisée pour une liste vide

---

### 3️ Cas récursif

```haskell
myMap f (x:xs) = f x : myMap f xs
```

* `(x:xs)` : tête `x`, reste `xs`
* `f x` → applique la fonction `f` à l’élément `x`
* `:` → ajoute ce résultat au début de la **liste résultat**
* `myMap f xs` → applique récursivement `f` sur le reste de la liste

---

### 4️ Exemple de déroulement

Liste : `[1,2,3]`
Fonction : `\x -> x * 2`

```
myMap (\x -> x*2) [1,2,3]
→ (1*2) : myMap (\x -> x*2) [2,3]
→ 2 : ((2*2) : myMap (\x -> x*2) [3])
→ 2 : (4 : ((3*2) : myMap (\x -> x*2) []))
→ 2 : (4 : (6 : []))
→ [2,4,6]
```

---

### 5️ Fonction `main`

* Définition d’une liste `[1,2,3,4,5]`
* Application de `myMap` avec la fonction `\x -> x*2` (double chaque élément)
* Affichage du résultat

###  Exemple de sortie

```
Liste originale : [1,2,3,4,5]
Liste après application de myMap (x*2) : [2,4,6,8,10]
```

---


Veux‑tu que je fasse ça ?
