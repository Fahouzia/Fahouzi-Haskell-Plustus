**HC13T3 : Trier et retourner les fichiers filtrés**

---
###  **Objectif**

Créer un programme qui :

1. Liste tous les fichiers du répertoire courant,
2. Filtre ceux contenant une **sous-chaîne donnée** dans leur nom,
3. **Trie** les fichiers correspondants par ordre alphabétique,
4. Et les affiche dans le terminal.

 On utilisera les fonctions **`filter`** et **`sort`** du module `Data.List`.

---

### **Code**

```haskell
-- HC13T3 : Trier et retourner les fichiers filtrés

import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (isInfixOf, sort)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "=== Trier et retourner les fichiers filtrés du répertoire courant ==="

    -- Obtenir le répertoire courant
    currentDir <- getCurrentDirectory
    putStrLn ("Répertoire actuel : " ++ currentDir)

    -- Lister le contenu du répertoire
    contents <- listDirectory currentDir

    -- Demander la sous-chaîne à rechercher
    putStrLn "\nEntrez une sous-chaîne à rechercher :"
    keyword <- getLine

    -- Filtrer les fichiers contenant la sous-chaîne
    let filtered = filter (isInfixOf keyword) contents

    -- Trier les résultats
    let sortedFiles = sort filtered

    -- Afficher les résultats triés
    putStrLn "\nFichiers correspondants (triés) :"
    if null sortedFiles
        then putStrLn "Aucun fichier ne correspond à cette sous-chaîne."
        else mapM_ putStrLn sortedFiles
```

---

### 🔍 **Explication pas à pas**

1. **Import des modules**

   ```haskell
   import System.Directory (getCurrentDirectory, listDirectory)
   import Data.List (isInfixOf, sort)
   ```

   * `listDirectory` : liste les fichiers/dossiers du répertoire courant.
   * `isInfixOf` : vérifie si une sous-chaîne est contenue dans une autre.
   * `sort` : trie une liste de chaînes de caractères par ordre alphabétique.

2. **Lecture de la sous-chaîne**

   ```haskell
   keyword <- getLine
   ```

3. **Filtrage**

   ```haskell
   let filtered = filter (isInfixOf keyword) contents
   ```

   → Garde uniquement les fichiers contenant la sous-chaîne saisie.

4. **Tri**

   ```haskell
   let sortedFiles = sort filtered
   ```

   → Trie la liste des fichiers retenus par ordre alphabétique (A → Z).

5. **Affichage du résultat**

   ```haskell
   mapM_ putStrLn sortedFiles
   ```

   → Affiche les fichiers ligne par ligne.

---

###  **Exemple d’exécution**

```
=== Trier et retourner les fichiers filtrés du répertoire courant ===
Répertoire actuel : /home/fahouzia/projets/haskell

Entrez une sous-chaîne à rechercher :
hs

Fichiers correspondants (triés) :
HC13T1.hs
HC13T2.hs
Main.hs
MathOperations.hs
```

---

