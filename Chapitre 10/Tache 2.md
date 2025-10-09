HC10T2 : Classe de type Summable

```haskell
-- Définition de la classe Summable
class Summable a where
    sumUp :: [a] -> a

-- Instance de Summable pour Int
instance Summable Int where
    sumUp []     = 0
    sumUp (x:xs) = x + sumUp xs

-- Fonction main pour tester sumUp
main :: IO ()
main = do
    let numbers = [1, 2, 3, 4, 5]
    putStrLn $ "La somme des nombres est : " ++ show (sumUp numbers)
```

---

### Explication ligne par ligne

1. ```haskell
   class Summable a where
       sumUp :: [a] -> a
   ```

   * On définit une **classe de type** `Summable`.
   * Tout type `a` qui devient instance de `Summable` doit définir `sumUp`, qui prend une liste de `a` et renvoie un élément de type `a` (la somme).

2. ```haskell
   instance Summable Int where
       sumUp []     = 0
       sumUp (x:xs) = x + sumUp xs
   ```

   * On rend `Int` une instance de `Summable`.
   * Pour une liste vide, la somme est `0`.
   * Pour une liste non vide `(x:xs)`, on ajoute `x` à la somme des éléments restants `sumUp xs`.
   * C’est une **définition récursive classique** pour la somme d’une liste.

3. ```haskell
   main :: IO ()
   main = do
       let numbers = [1, 2, 3, 4, 5]
       putStrLn $ "La somme des nombres est : " ++ show (sumUp numbers)
   ```

   * On crée une liste d’entiers.
   * On affiche le résultat de `sumUp numbers`.
   * Résultat attendu :

     ```
     La somme des nombres est : 15
     ```

---
