**HC14T10 : Test suite Cabal pour la fonction `counts`**.


##  **Objectif**

Créer une **suite de tests Cabal** qui vérifie le bon fonctionnement de la fonction `counts` définie précédemment.

---

##  **Structure du projet**

Ton projet doit ressembler à ceci :

```
my-project/
├── my-project.cabal
├── app/
│   └── Main.hs
├── src/
│   └── Lib.hs
└── test/
    └── Spec.hs
```

---

##  **1. Code de la bibliothèque (`src/Lib.hs`)**

```haskell
module Lib (counts) where

import Data.List (sort, group)

-- Fonction de comptage de fréquence des caractères
counts :: String -> [(Char, Int)]
counts str = [(head g, length g) | g <- group (sort str)]
```

---

##  **2. Code du test (`test/Spec.hs`)**

```haskell
module Main (main) where

import Test.Hspec
import Lib (counts)

main :: IO ()
main = hspec $ do
  describe "counts" $ do
    it "compte correctement les caractères de 'haskell'" $
      counts "haskell" `shouldBe` [('a',1),('e',1),('h',1),('k',1),('l',2),('s',1)]

    it "renvoie une liste vide pour une chaîne vide" $
      counts "" `shouldBe` []

    it "compte les espaces aussi" $
      counts "a a" `shouldBe` [(' ',1),('a',2)]
```

> On utilise ici **Hspec**, le framework de tests le plus courant en Haskell.

---

## ⚙️ **3. Modifier le fichier `.cabal`**

Ajoute la section **test-suite** à la fin de ton fichier `my-project.cabal` :

```cabal
cabal-version:       >=1.24
name:                my-project
version:             0.1.0.0
build-type:          Simple

library
  hs-source-dirs: src
  exposed-modules: Lib
  build-depends:
      base >=4.7 && <5
  default-language: Haskell2010

executable my-project-exe
  hs-source-dirs: app
  main-is: Main.hs
  build-depends:
      base >=4.7 && <5,
      my-project
  default-language: Haskell2010

-- =============================
--       SUITE DE TESTS
-- =============================
test-suite my-project-test
  type: exitcode-stdio-1.0
  hs-source-dirs: test
  main-is: Spec.hs
  build-depends:
      base >=4.7 && <5,
      hspec,
      my-project
  default-language: Haskell2010
```

---

##  **4. Installer la dépendance Hspec**

Ajoute dans le fichier `.cabal` ou via terminal :

```bash
cabal install --lib hspec
```

---

##  **5. Lancer la suite de tests**

Commande :

```bash
cabal test
```

---

##  **Résultat attendu**

```
counts
  compte correctement les caractères de 'haskell'
  renvoie une liste vide pour une chaîne vide
  compte les espaces aussi

Finished in 0.0003 seconds
3 examples, 0 failures
```

