**HC12T8 : Fusionner deux listes triées**

---

###  **Objectif**

Créer une fonction `mergeLists` qui **fusionne deux listes triées**
(par ordre croissant) en **une seule liste triée**, puis la tester dans `main`.

---

###  **Code **

```haskell
-- HC12T8 : Fusionner deux listes triées

-- Définition de la fonction mergeLists
mergeLists :: Ord a => [a] -> [a] -> [a]
mergeLists [] ys = ys
mergeLists xs [] = xs
mergeLists (x:xs) (y:ys)
    | x <= y    = x : mergeLists xs (y:ys)
    | otherwise = y : mergeLists (x:xs) ys

-- Fonction principale pour tester la fusion
main :: IO ()
main = do
    putStrLn "=== Fusion de deux listes triées ==="
    let list1 = [1, 3, 5, 7]
    let list2 = [2, 4, 6, 8, 10]
    let merged = mergeLists list1 list2
    putStrLn ("Liste 1 : " ++ show list1)
    putStrLn ("Liste 2 : " ++ show list2)
    putStrLn ("Liste fusionnée : " ++ show merged)
```

---

###  **Explication pas à pas**

1. **Signature de type :**

   ```haskell
   mergeLists :: Ord a => [a] -> [a] -> [a]
   ```

   * `Ord a` : le type `a` doit être comparable (`<=`).
   * La fonction prend **deux listes triées** et renvoie **une seule liste triée**.

2. **Cas de base :**

   ```haskell
   mergeLists [] ys = ys
   mergeLists xs [] = xs
   ```

   * Si l’une des deux listes est vide, la fusion est simplement l’autre liste.

3. **Cas récursif :**

   ```haskell
   mergeLists (x:xs) (y:ys)
       | x <= y    = x : mergeLists xs (y:ys)
       | otherwise = y : mergeLists (x:xs) ys
   ```

   * Compare les premiers éléments :

     * Si `x` est plus petit ou égal, on le garde en premier et on continue avec le reste de la première liste.
     * Sinon, on garde `y` en premier.

4. **Test dans `main` :**

   * Deux listes triées sont définies.
   * On les fusionne avec `mergeLists`.
   * Le résultat est affiché à l’écran.

---

###  **Exemple d’exécution**

```
=== Fusion de deux listes triées ===
Liste 1 : [1,3,5,7]
Liste 2 : [2,4,6,8,10]
Liste fusionnée : [1,2,3,4,5,6,7,8,10]
```

---
