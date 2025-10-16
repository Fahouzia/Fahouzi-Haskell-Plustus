

---

## Étape 1 : Ajouter la dépendance `random`

Ouvre ton fichier `.cabal` (par exemple `hello-cabal.cabal`) et modifie la section de l’exécutable pour inclure `random` :

```cabal
executable hello-cabal
  main-is:           Main.hs
  hs-source-dirs:    src
  build-depends:     base >=4.14 && <5,
                     random >=1.2
  default-language:  Haskell2010
```

* `build-depends` : liste les dépendances nécessaires pour ton projet.
* `random >=1.2` : version minimale du paquet `random`.

---

## Étape 2 : Modifier `Main.hs` pour générer un nombre aléatoire

Remplace le contenu de `src/Main.hs` par le code suivant :

```haskell
module Main where

import System.Random (randomRIO)

main :: IO ()
main = do
    -- Générer un nombre aléatoire entre 1 et 100
    nombre <- randomRIO (1, 100)
    putStrLn $ "Nombre aléatoire entre 1 et 100 : " ++ show nombre
```

**Explication :**

* `import System.Random (randomRIO)` : importe la fonction `randomRIO` pour générer des nombres aléatoires.
* `randomRIO (1, 100)` : retourne un nombre aléatoire entier entre 1 et 100 inclus.
* `<-` : récupère le résultat de l’action IO dans la variable `nombre`.
* `putStrLn $ "..." ++ show nombre` : affiche le nombre aléatoire.

---

## Étape 3 : Compiler et exécuter

Dans le terminal :

```bash
cabal build
cabal run
```

Exemple de sortie possible :

```
Nombre aléatoire entre 1 et 100 : 57
```

Chaque exécution donnera un nombre différent.

---

Si tu veux, je peux te créer **une version Cabal complète “clé en main”** avec `random` déjà configuré, que tu pourras juste compiler et exécuter.

Veux-tu que je fasse ça ?
