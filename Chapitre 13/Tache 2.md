**HC13T2 : Filtrer les fichiers par sous-chaîne**
---

###  **Objectif**

Créer un programme qui :

1. Liste les fichiers du répertoire courant,
2. Demande à l’utilisateur une **sous-chaîne à rechercher**,
3. Affiche uniquement les fichiers **dont le nom contient cette sous-chaîne**,
4. Utilise la fonction **`isInfixOf`** du module `Data.List`.

---

###  **Code**

```haskell
-- HC13T2 : Filtrer les fichiers par sous-chaîne

import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (isInfixOf)

main :: IO ()
main = do
    putStrLn "=== Filtrer les fichiers du répertoire courant par sous-chaîne ==="

    -- Obtenir le répertoire courant
    currentDir <- getCurrentDirectory
    putStrLn ("Répertoire actuel : " ++ currentDir)

    -- Lister tous les fichiers et dossiers
    contents <- listDirectory currentDir

    -- Demander la sous-chaîne à chercher
    putStrLn "\nEntrez une sous-chaîne à rechercher dans les noms de fichiers :"
    keyword <- getLine

    -- Filtrer les fichiers dont le nom contient la sous-chaîne
    let filtered = filter (isInfixOf keyword) contents

    -- Afficher le résultat
    putStrLn "\nRésultats :"
    if null filtered
        then putStrLn "Aucun fichier ne correspond à cette sous-chaîne."
        else mapM_ putStrLn filtered
```

---

###  **Explication pas à pas**

1. **Imports nécessaires**

   ```haskell
   import System.Directory (getCurrentDirectory, listDirectory)
   import Data.List (isInfixOf)
   ```

   * `getCurrentDirectory` → récupère le dossier où le programme s’exécute.
   * `listDirectory` → liste tous les fichiers/dossiers.
   * `isInfixOf` → vérifie si une sous-chaîne est présente dans une autre chaîne.
     Exemple : `isInfixOf "txt" "notes.txt"` → `True`.

2. **Lecture de la sous-chaîne**

   ```haskell
   keyword <- getLine
   ```

   L’utilisateur tape, par exemple, `hs` pour trouver tous les fichiers Haskell.

3. **Filtrage**

   ```haskell
   let filtered = filter (isInfixOf keyword) contents
   ```

   On parcourt la liste de fichiers et on ne garde que ceux dont le nom contient `keyword`.

4. **Affichage des résultats**

   * Si aucun fichier trouvé → message adapté.
   * Sinon → affiche la liste des fichiers correspondants.

---

###  **Exemple d’exécution**

```
=== Filtrer les fichiers du répertoire courant par sous-chaîne ===
Répertoire actuel : /home/fahouzia/projets/haskell

Entrez une sous-chaîne à rechercher dans les noms de fichiers :
hs

Résultats :
Main.hs
MathOperations.hs
```
