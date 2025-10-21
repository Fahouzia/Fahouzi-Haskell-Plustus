 **HC16T3 : Factorielle** — un grand classique des fonctions récursives en Haskell.

---

###  Objectif

Créer une fonction `factorial` qui calcule la **factorielle** d’un nombre donné.

 **Rappel mathématique :**
( n! = n \times (n - 1) \times (n - 2) \times \dots \times 1 )
Et par convention :
( 0! = 1 )

---

###  Code
```haskell
-- HC16T3 : Factorielle d’un nombre

-- Définition récursive de la factorielle
factorial :: Integer -> Integer
factorial 0 = 1
factorial n = n * factorial (n - 1)

-- Programme principal pour tester
main :: IO ()
main = do
    putStrLn "=== Calcul de la factorielle ==="
    putStrLn "Entrez un nombre entier :"
    input <- getLine
    let n = read input :: Integer
    putStrLn ("La factorielle de " ++ show n ++ " est : " ++ show (factorial n))
```

---

###  Explications détaillées

1. **Signature de la fonction**

   ```haskell
   factorial :: Integer -> Integer
   ```

   Elle prend un entier (`Integer`) et retourne un entier (`Integer`).

2. **Cas de base**

   ```haskell
   factorial 0 = 1
   ```

   C’est la condition d’arrêt de la récursion (0! = 1).

3. **Cas récursif**

   ```haskell
   factorial n = n * factorial (n - 1)
   ```

   On multiplie `n` par la factorielle du nombre précédent.

4. **Bloc `main`**

   * Lecture d’un nombre.
   * Conversion en entier avec `read`.
   * Affichage du résultat calculé.

---

### 🧩 Exemples d’exécution

✅ **Cas normal :**

```
=== Calcul de la factorielle ===
Entrez un nombre entier :
5
La factorielle de 5 est : 120
```

✅ **Cas 0 :**

```
Entrez un nombre entier :
0
La factorielle de 0 est : 1
```

---
