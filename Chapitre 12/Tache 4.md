**HC12T4 : Premiers 10 nombres de Fibonacci**

---

###  **Code **

```haskell
-- Définition de la fonction récursive Fibonacci
fibonacci :: Int -> Int
fibonacci 0 = 0
fibonacci 1 = 1
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)

-- Fonction principale main
main :: IO ()
main = do
    putStrLn "Les 10 premiers nombres de Fibonacci sont :"
    -- Génération d'une liste de 0 à 9 et calcul de chaque nombre
    let first10 = [fibonacci n | n <- [0..9]]
    print first10
```

---

### 🔍 **Explication pas à pas**

1. **Définition de la fonction récursive**

   ```haskell
   fibonacci :: Int -> Int
   fibonacci 0 = 0
   fibonacci 1 = 1
   fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)
   ```

   * La fonction prend un entier `n` et retourne le **n-ième nombre de Fibonacci**.
   * **Cas de base :**

     * `fibonacci 0 = 0`
     * `fibonacci 1 = 1`
   * **Cas récursif :**

     * `fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)`
       → Chaque nombre est la somme des deux nombres précédents.

---

2. **Génération des 10 premiers nombres**

   ```haskell
   let first10 = [fibonacci n | n <- [0..9]]
   ```

   * `[0..9]` génère la liste `[0,1,2,...,9]`.
   * Pour chaque `n`, on calcule `fibonacci n` et on obtient la liste des 10 premiers nombres de Fibonacci.

---

3. **Affichage**

   ```haskell
   print first10
   ```

   * Affiche la liste complète dans le terminal.

---

###  **Exemple d’exécution**

```
Les 10 premiers nombres de Fibonacci sont :
[0,1,1,2,3,5,8,13,21,34]
```

---
Veux‑tu que je fasse ça ?
