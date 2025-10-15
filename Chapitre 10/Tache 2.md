HC10T2 : Classe de type Summable

```haskell
-- HC10T2 : Classe Summable

-- Définition de la classe Summable
class Summable a where
    sumUp :: [a] -> a

-- Implémentation pour Int
instance Summable Int where
    sumUp []     = 0
    sumUp (x:xs) = x + sumUp xs

-- Fonction principale pour tester
main :: IO ()
main = do
    let liste1 = [1,2,3,4,5]
    let liste2 = [10,20,30]
    putStrLn ("Somme de [1,2,3,4,5] : " ++ show (sumUp liste1))
    putStrLn ("Somme de [10,20,30]   : " ++ show (sumUp liste2))

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
