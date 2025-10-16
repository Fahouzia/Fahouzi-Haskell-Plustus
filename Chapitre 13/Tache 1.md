**HC13T1 : Lister les fichiers du répertoire courant**

---

###  **Objectif**

Créer un programme Haskell qui :

1. Utilise le module **`System.Directory`**
2. Liste **tous les fichiers et dossiers** présents dans le **répertoire courant** (où le programme est exécuté)
3. Les affiche proprement dans le terminal.

---

###  **Code**

```haskell
-- HC13T1 : Lister les fichiers du répertoire courant

import System.Directory (getCurrentDirectory, listDirectory)
import System.FilePath ((</>))

main :: IO ()
main = do
    putStrLn "=== Liste des fichiers du répertoire courant ==="

    -- Obtenir le chemin du répertoire courant
    currentDir <- getCurrentDirectory
    putStrLn ("Répertoire actuel : " ++ currentDir)

    -- Lister le contenu du répertoire
    contents <- listDirectory currentDir

    -- Afficher les fichiers trouvés
    putStrLn "\nContenu du répertoire :"
    mapM_ putStrLn contents
```

---

###  **Explication pas à pas**

1. **Import des modules**

   ```haskell
   import System.Directory (getCurrentDirectory, listDirectory)
   import System.FilePath ((</>))
   ```

   * `getCurrentDirectory` → renvoie le chemin absolu du répertoire courant.
   * `listDirectory` → renvoie une liste contenant les noms des fichiers et dossiers du répertoire.
   * `</>` → permet de combiner proprement des chemins (facultatif ici, mais utile pour des extensions futures).

2. **Récupération du répertoire courant**

   ```haskell
   currentDir <- getCurrentDirectory
   ```

   Exemple : `/home/fahouzia/Documents`

3. **Liste du contenu**

   ```haskell
   contents <- listDirectory currentDir
   ```

   Cela renvoie une liste comme `["Main.hs", "data.txt", "Images"]`.

4. **Affichage ligne par ligne**

   ```haskell
   mapM_ putStrLn contents
   ```

   `mapM_` applique `putStrLn` à chaque élément de la liste (affichage sans retour de liste).

---

###  **Exemple d’exécution**

```
=== Liste des fichiers du répertoire courant ===
Répertoire actuel : /home/fahouzia/projets/haskell

Contenu du répertoire :
Main.hs
MathOperations.hs
notes.txt
Images
```
