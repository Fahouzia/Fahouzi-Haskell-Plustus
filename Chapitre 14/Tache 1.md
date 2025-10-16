**HC14T1** avec **Cabal**

---

## Étape 1 : Initialiser le projet Cabal

1. Ouvrez un terminal.
2. Créez un dossier pour votre projet, par exemple `HelloCabal` :

```bash
mkdir HelloCabal
cd HelloCabal
```

3. Initialisez un projet Cabal avec l’option interactive (pour guider la configuration) :

```bash
cabal init
```

Vous serez invité à répondre à plusieurs questions :

* **Package name** : `hello-cabal`
* **Package type** : `Executable`
* **Main module** : laissez `Main.hs`
* **Source directory** : `src`
* **License** : choisissez `MIT` ou `AllRightsReserved`
* **Author / Maintainer / Synopsis / Description** : remplissez comme vous voulez
* Les autres options peuvent rester par défaut.

Cabal va créer la structure suivante :

```
HelloCabal/
├─ hello-cabal.cabal
├─ src/
│  └─ Main.hs
└─ dist-newstyle/
```

---

## Étape 2 : Écrire le code de l’exécutable

Ouvrez `src/Main.hs` et remplacez son contenu par :

```haskell
module Main where

main :: IO ()
main = putStrLn "Hello, Cabal!"
```

**Explication :**

* `module Main where` : définit le module principal.
* `main :: IO ()` : `main` est une action IO qui ne retourne rien (`()` est le type unit).
* `putStrLn "Hello, Cabal!"` : affiche le texte à l’écran suivi d’un retour à la ligne.

---

## Étape 3 : Compiler et exécuter le projet

1. Dans le terminal, compilez le projet :

```bash
cabal build
```

2. Exécutez le programme :

```bash
cabal run
```

Vous devriez voir :

```
Hello, Cabal!
```

---

 **Résumé :**

* Création du projet avec `cabal init`
* Définition de l’exécutable principal `Main.hs`
* Compilation avec `cabal build`
* Exécution avec `cabal run`



---

### 1️ `src/Main.hs`

```haskell
module Main where

main :: IO ()
main = putStrLn "Hello, Cabal!"
```

---

### 2️ Structure Cabal minimale (`hello-cabal.cabal`)

```cabal
cabal-version:       3.2
name:                hello-cabal
version:             0.1.0.0
build-type:          Simple
license:             MIT
author:              TonNom
maintainer:          ton.email@example.com
synopsis:            Exemple de projet Cabal
category:            Example

executable hello-cabal
  main-is:           Main.hs
  hs-source-dirs:    src
  build-depends:     base >=4.14 && <5
  default-language:  Haskell2010
```

---

### 3️ Commandes pour compiler et exécuter

```bash
cabal build
cabal run
```

**Sortie attendue :**

```
Hello, Cabal!
```

---

