**HC16T6 : n-ième nombre de Fibonacci**
 
---

###  Objectif

Créer une fonction qui retourne le **n-ième nombre de Fibonacci**, avec la suite :

[
F_0 = 0, \quad F_1 = 1, \quad F_n = F_{n-1} + F_{n-2} \text{ pour } n \ge 2
]

Exemples :

* n = 0 → 0
* n = 1 → 1
* n = 5 → 5 (suite : 0, 1, 1, 2, 3, 5, 8…)

---

###  Code

```haskell
-- HC16T6 : n-ième nombre de Fibonacci

-- Fonction récursive
fibonacci :: Integer -> Integer
fibonacci 0 = 0
fibonacci 1 = 1
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)

-- Programme principal pour tester
main :: IO ()
main = do
    putStrLn "=== Calcul du n-ième nombre de Fibonacci ==="
    putStrLn "Entrez n :"
    input <- getLine
    let n = read input :: Integer
    putStrLn ("Le " ++ show n ++ "-ième nombre de Fibonacci est : " ++ show (fibonacci n))
```

---

### 🔍 Explications

1. **Cas de base**

```haskell
fibonacci 0 = 0
fibonacci 1 = 1
```

* Ce sont les deux premiers nombres de la suite.

2. **Cas récursif**

```haskell
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)
```

* Chaque terme est la somme des deux précédents.

3. **Bloc `main`**

* Lit un entier n.
* Affiche le n-ième nombre de Fibonacci.

---

### 🧩 Exemple d’exécution

```
=== Calcul du n-ième nombre de Fibonacci ===
Entrez n :
7
Le 7-ième nombre de Fibonacci est : 13
```

---

