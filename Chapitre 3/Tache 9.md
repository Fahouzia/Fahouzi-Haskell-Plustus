HC3T9 : Trouver le maximum de trois nombres avec let

```haskell

maxOfThree :: Int -> Int -> Int -> Int
maxOfThree a b c =
    let maxAB = if a > b then a else b
        maxABC = if maxAB > c then maxAB else c
    in maxABC

main :: IO ()
main = do
    putStrLn ("maxOfThree 10 20 15 → " ++ show (maxOfThree 10 20 15))
    putStrLn ("maxOfThree 5 25 10  → " ++ show (maxOfThree 5 25 10))
```

---

*Résultat*

```
maxOfThree 10 20 15 → 20
maxOfThree 5 25 10  → 25
```

---

**Explication détaillée**

###  1. Signature de la fonction

```haskell
maxOfThree :: Int -> Int -> Int -> Int
```

 La fonction prend **trois entiers (`Int`)** en entrée
et retourne **un entier** : le plus grand des trois.

---

###  2. Utilisation de `let … in`

```haskell
let maxAB = if a > b then a else b
    maxABC = if maxAB > c then maxAB else c
in maxABC
```

`let … in` sert à **définir des variables locales** dans une expression Haskell.

Ici :

* `maxAB` → le plus grand entre `a` et `b`
* `maxABC` → le plus grand entre `maxAB` et `c`

Enfin, la fonction **retourne `maxABC`**.

---

###  3. Fonction `main`

```haskell
main = do
    putStrLn ("maxOfThree 10 20 15 → " ++ show (maxOfThree 10 20 15))
```

 `putStrLn` affiche du texte à l’écran.
 `show` convertit le nombre (résultat de la fonction) en **chaîne de caractères**,
car `putStrLn` ne peut afficher que des chaînes.

---
1. On compare d’abord les deux premiers nombres.
2. On compare ensuite le résultat au troisième.
3. Le plus grand des trois est retourné.
