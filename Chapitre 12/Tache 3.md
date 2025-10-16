**HC12T3 : Fonction factorielle**, avec **explications détaillées pas à pas** 

---

###  **Code**

```haskell
-- Définition de la fonction factorielle
factorial :: Int -> Int
factorial 0 = 1
factorial n = n * factorial (n - 1)

-- Fonction principale main
main :: IO ()
main = do
    putStrLn "Entrez un nombre entier positif :"
    input <- getLine
    let n = read input :: Int

    let result = factorial n

    putStrLn ("La factorielle de " ++ show n ++ " est : " ++ show result)
```

---

### 🔍 **Explication pas à pas**

1. **Définition de la fonction récursive**

   ```haskell
   factorial :: Int -> Int
   factorial 0 = 1
   factorial n = n * factorial (n - 1)
   ```

   * On déclare que `factorial` prend un entier (`Int`) et retourne un entier.
   * **Cas de base :** `factorial 0 = 1`
     → La factorielle de 0 est toujours 1.
   * **Cas récursif :** `factorial n = n * factorial (n - 1)`
     → On multiplie `n` par la factorielle du nombre précédent.

---

2. **Lecture de l’entrée utilisateur**

   ```haskell
   input <- getLine
   let n = read input :: Int
   ```

   * `getLine` lit la saisie de l’utilisateur sous forme de texte (`String`),
   * `read` convertit ce texte en entier (`Int`).

---

3. **Appel de la fonction et affichage**

   ```haskell
   let result = factorial n
   putStrLn ("La factorielle de " ++ show n ++ " est : " ++ show result)
   ```

   * `show` convertit le résultat numérique en texte pour l’afficher correctement.

---

### **Exemple d’exécution**

```
Entrez un nombre entier positif :
5
La factorielle de 5 est : 120
```

---
