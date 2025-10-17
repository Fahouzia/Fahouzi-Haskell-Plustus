**HC14T6 : Structure du projet avec `src` et `app`** 

---

##  **Objectif**

Créer une **structure standard de projet Cabal** avec :

* le **module principal** dans `app/`
* les **autres modules** dans `src/`

---

##  **1. Structure du projet**

Organise ton projet ainsi :

```
my-project/
│
├── my-project.cabal
├── cabal.project
│
├── app/
│   └── Main.hs
│
└── src/
    └── Lib.hs
```

---

## 📝 **2. Fichier `my-project.cabal`**

Voici un modèle complet à copier :

```cabal
cabal-version:       >=1.24
name:                my-project
version:             0.1.0.0
author:              Ton Nom
maintainer:          ton.email@example.com
build-type:          Simple

-- =====================
--  Composant bibliothèque
-- =====================
library
  hs-source-dirs: src
  exposed-modules: Lib
  build-depends:
      base >=4.7 && <5
  default-language: Haskell2010

-- =====================
--  Composant exécutable
-- =====================
executable my-project-exe
  hs-source-dirs: app
  main-is: Main.hs
  build-depends:
      base >=4.7 && <5,
      my-project
  default-language: Haskell2010
```

---

## 💻 **3. Code du module principal – `app/Main.hs`**

```haskell
module Main where

import Lib (sayHello)

main :: IO ()
main = putStrLn (sayHello "Cabal")
```

---

## 💡 **4. Code du module secondaire – `src/Lib.hs`**

```haskell
module Lib (sayHello) where

sayHello :: String -> String
sayHello name = "Bonjour, " ++ name ++ " !"
```

---

## ▶️ **5. Exécution**

Dans le terminal :

```bash
cabal build
cabal run my-project-exe
```

 **Résultat attendu :**

```
Bonjour, Cabal !
```

-
