 **HC14T7 : Composant bibliothèque dans le `.cabal`**

---

###  **Objectif**

Modifier le fichier `.cabal` de ton projet pour :

* Ajouter un **composant bibliothèque** (`library`) qui contient ton code réutilisable.
* Garder un **exécutable principal** (`executable`) qui utilise cette bibliothèque.

---

###  **Structure de ton projet**

Assurons-nous que le projet est organisé comme suit :

```
my-project/
│
├── my-project.cabal
├── cabal.project
├── app/
│   └── Main.hs
└── src/
    └── Lib.hs
```

* `src/Lib.hs` contiendra les fonctions exportées par ta bibliothèque.
* `app/Main.hs` sera ton exécutable principal qui importe `Lib`.

---

###  **code .cabal**



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
      my-project        -- <--- dépend de la bibliothèque
  default-language: Haskell2010
```

---

###  **Code**

**src/Lib.hs**

```haskell
module Lib (sayHello) where

sayHello :: String -> String
sayHello name = "Bonjour, " ++ name ++ " !"
```

**app/Main.hs**

```haskell
module Main where

import Lib (sayHello)

main :: IO ()
main = putStrLn (sayHello "Haskell")
```

---

### **Exécution**

Compile et exécute :

```bash
cabal build
cabal run my-project-exe
```

 **Résultat attendu :**

```
Bonjour, Haskell !
```

---
