 **HC13T10 : Fonction main multi-modules**

---

##  **Objectif**

1. Utiliser **au moins deux modules** : `System.Directory` pour manipuler les fichiers et `Data.List` pour trier les résultats.
2. Créer une fonction `main` qui :

   * Liste les fichiers du répertoire courant,
   * Filtre les fichiers contenant une **sous-chaîne donnée**,
   * Trie les résultats,
   * Affiche la liste triée.

---

##  **Code**

```haskell
-- HC13T10 : Fonction main multi-modules
import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (isInfixOf, sort)

main :: IO ()
main = do
    putStrLn "=== HC13T10 : Recherche et tri de fichiers ==="

    -- Récupérer le répertoire courant
    currentDir <- getCurrentDirectory
    putStrLn ("Répertoire actuel : " ++ currentDir)

    -- Lister le contenu du répertoire
    files <- listDirectory currentDir

    -- Demander la sous-chaîne à rechercher
    putStrLn "\nEntrez une sous-chaîne pour filtrer les fichiers :"
    keyword <- getLine

    -- Filtrer les fichiers contenant la sous-chaîne
    let filteredFiles = filter (isInfixOf keyword) files

    -- Trier les fichiers
    let sortedFiles = sort filteredFiles

    -- Afficher les résultats triés
    putStrLn "\nFichiers correspondants (triés) :"
    if null sortedFiles
        then putStrLn "Aucun fichier ne correspond à cette sous-chaîne."
        else mapM_ putStrLn sortedFiles
```

---

##  **Explication pas à pas**

1. **Imports des modules**

```haskell
import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (isInfixOf, sort)
```

* `System.Directory` : pour **obtenir le répertoire courant** et **lister les fichiers**.
* `Data.List` : pour **filtrer** (`isInfixOf`) et **trier** (`sort`) les fichiers.

2. **Liste des fichiers**

```haskell
files <- listDirectory currentDir
```

* Récupère tous les fichiers et dossiers du répertoire courant.

3. **Filtrage**

```haskell
let filteredFiles = filter (isInfixOf keyword) files
```

* Garde uniquement les fichiers dont le nom contient la **sous-chaîne** saisie par l’utilisateur.

4. **Tri**

```haskell
let sortedFiles = sort filteredFiles
```

* Trie les fichiers par ordre alphabétique.

5. **Affichage**

```haskell
mapM_ putStrLn sortedFiles
```

* Affiche chaque fichier sur une nouvelle ligne.
* Si la liste est vide, un message adapté est affiché.

---

##  **Exemple d’exécution**

```
=== HC13T10 : Recherche et tri de fichiers ===
Répertoire actuel : /home/fahouzia/projets/haskell

Entrez une sous-chaîne pour filtrer les fichiers :
hs

Fichiers correspondants (triés) :
HC13T1.hs
HC13T2.hs
Main.hs
MathOperations.hs
```
