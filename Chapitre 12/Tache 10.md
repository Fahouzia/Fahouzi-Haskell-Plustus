**HC12T10 : Module d’opérations mathématiques**

---

###  **Objectif**

Créer :

1. Un **module séparé** qui définit des **opérations mathématiques** (addition, soustraction, multiplication, division).
2. Un **programme principal (`main`)** qui **importe ce module** et **utilise ses fonctions**.

---

###  **Structure du projet**

Tu dois créer **deux fichiers Haskell** dans le même dossier :

```
MathOperations.hs
Main.hs
```

---

##  **Fichier 1 : MathOperations.hs**

```haskell
-- HC12T10 : Module d’opérations mathématiques
module MathOperations
( add
, subtract'
, multiply
, divide
) where

-- Addition
add :: Float -> Float -> Float
add x y = x + y

-- Soustraction (nommée subtract' pour éviter conflit avec Prelude.subtract)
subtract' :: Float -> Float -> Float
subtract' x y = x - y

-- Multiplication
multiply :: Float -> Float -> Float
multiply x y = x * y

-- Division (avec gestion de division par zéro)
divide :: Float -> Float -> Float
divide _ 0 = error "Erreur : division par zéro !"
divide x y = x / y
```

---

##  **CODE**

```haskell
-- Programme principal qui utilise le module MathOperations
import MathOperations

main :: IO ()
main = do
    putStrLn "=== Module d’opérations mathématiques ==="
    putStrLn "Entrez le premier nombre :"
    input1 <- getLine
    putStrLn "Entrez le deuxième nombre :"
    input2 <- getLine

    let a = read input1 :: Float
    let b = read input2 :: Float

    putStrLn ("\nRésultats :")
    putStrLn ("Addition : " ++ show (add a b))
    putStrLn ("Soustraction : " ++ show (subtract' a b))
    putStrLn ("Multiplication : " ++ show (multiply a b))
    putStrLn ("Division : " ++ show (divide a b))
```

---

###  **Comment exécuter**

Dans ton terminal Haskell (ou GHCi) :

```bash
ghci Main.hs
```

Puis exécute :

```haskell
main
```

---

###  **Exemple d’exécution**

```
=== Module d’opérations mathématiques ===
Entrez le premier nombre :
12
Entrez le deuxième nombre :
4

Résultats :
Addition : 16.0
Soustraction : 8.0
Multiplication : 48.0
Division : 3.0
```

---

###  **Explication du fonctionnement**

1. **`module MathOperations (...) where`**
   → Définit un module exportant uniquement les fonctions listées entre parenthèses.

2. **Chaque fonction** (`add`, `subtract'`, etc.) effectue une opération arithmétique.

3. **`Main.hs` importe le module** :

   ```haskell
   import MathOperations
   ```

   et appelle directement ces fonctions.

4. **`divide`** gère la division par zéro pour éviter une erreur d’exécution.

---
