**HC12T6 : Trier une liste d’entiers**
---

###  **Code **

```haskell
import Data.List (sort)

-- Fonction principale main
main :: IO ()
main = do
    putStrLn "Entrez des nombres séparés par des espaces :"
    input <- getLine

    -- Conversion de la chaîne en liste d'entiers
    let numbers = map read (words input) :: [Int]

    -- Tri de la liste
    let sortedNumbers = sort numbers

    -- Affichage du résultat
    putStrLn "La liste triée est :"
    print sortedNumbers
```

---

### 🔍 **Explication pas à pas**

1. **Importer la fonction `sort`**

   ```haskell
   import Data.List (sort)
   ```

   * `sort` permet de trier une liste d’éléments ordonnables (`Ord`).

---

2. **Lecture de l’entrée utilisateur**

   ```haskell
   input <- getLine
   ```

   * L’utilisateur entre une ligne de nombres séparés par des espaces, par exemple :

     ```
     5 2 9 1 7
     ```

---

3. **Conversion en liste d’entiers**

   ```haskell
   let numbers = map read (words input) :: [Int]
   ```

   * `words input` : transforme la chaîne en liste de chaînes, séparées par les espaces.
     Exemple : `"5 2 9 1 7"` → `["5","2","9","1","7"]`
   * `map read` : convertit chaque chaîne en entier.
     Résultat : `[5,2,9,1,7]`

---

4. **Tri de la liste**

   ```haskell
   let sortedNumbers = sort numbers
   ```

   * `sort` trie la liste dans l’ordre croissant.
   * Résultat : `[1,2,5,7,9]`

---

5. **Affichage**

   ```haskell
   putStrLn "La liste triée est :"
   print sortedNumbers
   ```

   * `print` affiche la liste triée.

---

###  **Exemple d’exécution**

```
Entrez des nombres séparés par des espaces :
5 2 9 1 7
La liste triée est :
[1,2,5,7,9]
```

---
