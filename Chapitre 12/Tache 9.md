**HC12T9 : Lire et afficher le contenu d’un fichier**

---

###  **Objectif**

Créer un programme qui :

1. Demande à l’utilisateur le **nom d’un fichier**,
2. **Lit** le contenu de ce fichier,
3. **Affiche** son contenu dans le terminal,
4. Et **gère les erreurs** si le fichier n’existe pas ou n’est pas accessible.

---

###  **Code**

```haskell
-- HC12T9 : Lire et afficher le contenu d’un fichier

import System.IO
import System.IO.Error (catchIOError)
import Control.Exception (IOException)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "=== Lecture et affichage du contenu d’un fichier ==="
    putStrLn "Entrez le nom du fichier à lire :"
    fileName <- getLine
    readFileSafe fileName

-- Fonction qui lit le fichier en gérant les erreurs
readFileSafe :: FilePath -> IO ()
readFileSafe fileName = do
    contentOrError <- catchIOError (do
        content <- readFile fileName
        putStrLn "\n--- Contenu du fichier ---"
        putStrLn content
        return ())
        handler
    return contentOrError
  where
    handler :: IOException -> IO ()
    handler e = putStrLn ("\nErreur : impossible de lire le fichier.\nDétails : " ++ show e)
```

---

###  **Explication pas à pas**

1. **Importation des modules nécessaires**

   ```haskell
   import System.IO
   import System.IO.Error (catchIOError)
   import Control.Exception (IOException)
   ```

   Ces modules permettent de lire des fichiers et d’intercepter proprement les erreurs.

2. **Lecture du nom du fichier**

   ```haskell
   fileName <- getLine
   ```

   On lit le nom du fichier tapé par l’utilisateur (ex : `"test.txt"`).

3. **Lecture avec gestion d’erreur**

   ```haskell
   catchIOError (do
       content <- readFile fileName
       putStrLn content)
       handler
   ```

   * `readFile` lit le contenu du fichier.
   * `catchIOError` intercepte les erreurs d’entrée/sortie (comme “fichier introuvable”).
   * `handler` affiche un message d’erreur au lieu de faire planter le programme.

4. **Affichage du contenu**

   ```haskell
   putStrLn "\n--- Contenu du fichier ---"
   putStrLn content
   ```

5. **Gestion des erreurs**

   ```haskell
   handler e = putStrLn ("\nErreur : impossible de lire le fichier.\nDétails : " ++ show e)
   ```

   Si le fichier n’existe pas, on affiche le message d’erreur complet.

---

###  **Exemple d’exécution réussie**

```
=== Lecture et affichage du contenu d’un fichier ===
Entrez le nom du fichier à lire :
notes.txt

--- Contenu du fichier ---
Bonjour Haskell !
Ceci est un test de lecture de fichier.
```

---

### **Exemple si le fichier n’existe pas**

```
=== Lecture et affichage du contenu d’un fichier ===
Entrez le nom du fichier à lire :
inexistant.txt

Erreur : impossible de lire le fichier.
Détails : inexistant.txt: openFile: does not exist (No such file or directory)
```

---
