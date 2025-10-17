**HC14T9 : Extension `PartialTypeSignatures`**.

---

##  **Objectif**

Activer l’extension `PartialTypeSignatures` et écrire une fonction dont la
**signature contient un joker (`_`)** pour laisser le compilateur **inférer une partie du type**.

---

##  **Étapes**

### 1️ Activer l’extension

Tu peux activer `PartialTypeSignatures` :

* soit **dans le code** avec une pragma :

  ```haskell
  {-# LANGUAGE PartialTypeSignatures #-}
  ```
* soit **dans ton fichier `.cabal`** :

  ```cabal
  ghc-options: -fpartial-type-signatures
  ```

---

### 2️ Exemple de code complet

```haskell
{-# LANGUAGE PartialTypeSignatures #-}

module Main where

-- Définition d'une fonction avec type partiel
addAndShow :: _ -> _ -> String
addAndShow x y = show (x + y)

main :: IO ()
main = do
  putStrLn (addAndShow 3 5)
  putStrLn (addAndShow 10 42)
```

---

###  **Explication**

* Le type `_` signifie “le compilateur peut deviner ce type”.
* Ici, Haskell infère :

  ```haskell
  addAndShow :: (Show a, Num a) => a -> a -> String
  ```

  … mais tu n’as pas besoin de l’écrire entièrement.

---

###  **Exécution**

```bash
cabal run my-project-exe
```

 **Résultat attendu :**

```
8
52
```

---

###  **Remarque**

Par défaut, GHC peut afficher un *warning* pour t’indiquer le type qu’il a déduit.
Si tu veux le **masquer**, ajoute cette option :

```haskell
{-# OPTIONS_GHC -fno-warn-partial-type-signatures #-}
```

