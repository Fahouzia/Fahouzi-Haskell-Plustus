 **HC14T5 : Type `Result a` et pattern matching avec le symbole `@`**.


##  **Objectif**

1. Créer un type de données paramétrique :

   ```haskell
   data Result a = Success a | Error String
   ```
2. Utiliser le **pattern matching avec `@`** pour nommer un motif tout en le déconstruisant.

---

##  **Code **

```haskell
module Main where

-- Définition d’un type générique Result
data Result a = Success a | Error String
  deriving (Show)

-- Fonction qui affiche le résultat avec pattern matching et alias @
describeResult :: Show a => Result a -> String
describeResult res@(Success val) =
  "Succès détecté : " ++ show val ++ " (alias complet : " ++ show res ++ ")"
describeResult err@(Error msg) =
  "Erreur détectée : " ++ msg ++ " (alias complet : " ++ show err ++ ")"

main :: IO ()
main = do
  let r1 = Success 42
  let r2 = Error "Division par zéro"
  putStrLn (describeResult r1)
  putStrLn (describeResult r2)
```

---

## 🧠 **Explication pas à pas**

* `data Result a = Success a | Error String`
  ➜ Définit un type générique qui peut représenter un succès ou une erreur.

* `res@(Success val)`
  ➜ Le symbole `@` crée un **alias de motif** :

  * `res` fait référence à la valeur complète (`Success 42`),
  * `val` fait référence à la partie interne (`42`).

* Idem pour `err@(Error msg)` :

  * `err` = `Error "Division par zéro"`
  * `msg` = `"Division par zéro"`

---

##  **Exécution**

```bash
cabal run my-project-exe
```

 **Résultat attendu :**

```
Succès détecté : 42 (alias complet : Success 42)
Erreur détectée : Division par zéro (alias complet : Error "Division par zéro")
```

---
