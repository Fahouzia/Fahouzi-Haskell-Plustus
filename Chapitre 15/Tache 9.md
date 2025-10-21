**HC15T9**, où tu vas apprendre à **intercepter proprement les exceptions d’entrée/sortie (IO)** 
---

###  Objectif

Créer un programme qui :

1. Demande à l’utilisateur le nom d’un fichier,
2. Tente de lire son contenu,
3. Utilise `try` pour **capturer les exceptions IO** (par exemple : fichier inexistant),
4. Affiche un message d’erreur clair si une exception se produit.

---

### Code 

```haskell
-- HC15T9 : Utiliser try pour intercepter les exceptions IO de fichier

import System.IO
import Control.Exception (try, IOException)

main :: IO ()
main = do
    putStrLn "=== Lecture de fichier sécurisée avec try ==="
    putStrLn "Entrez le nom du fichier à lire :"
    fileName <- getLine

    -- On tente de lire le fichier en interceptant les erreurs IO
    result <- try (readFile fileName) :: IO (Either IOException String)

    case result of
        Left err  -> putStrLn ("Erreur lors de la lecture du fichier : " ++ show err)
        Right content -> do
            putStrLn "Contenu du fichier :"
            putStrLn "---------------------"
            putStrLn content
```

---

###  Explications détaillées

1. **Importations nécessaires**

   ```haskell
   import Control.Exception (try, IOException)
   ```

   * `try` permet d’intercepter les exceptions dans une action IO.
   * `IOException` est le type des erreurs liées aux opérations sur les fichiers (lecture, écriture, etc.).

2. **Type de retour**

   ```haskell
   try (readFile fileName) :: IO (Either IOException String)
   ```

   * Si la lecture réussit → `Right contenu`
   * Si une exception se produit → `Left exception`

3. **Pattern matching sur le résultat**

   * `Left err` → Affiche le message d’erreur.
   * `Right content` → Affiche le contenu du fichier.

4. **Avantage**

   * Le programme **ne s’arrête pas brutalement** en cas d’erreur (comme fichier introuvable).
   * Il affiche un message clair et continue à s’exécuter.

---

###  Exemples d’exécution

**Cas fichier existant :**

```
=== Lecture de fichier sécurisée avec try ===
Entrez le nom du fichier à lire :
notes.txt
Contenu du fichier :
---------------------
Bonjour, ceci est un fichier de test.
```

 **Cas fichier inexistant :**

```
=== Lecture de fichier sécurisée avec try ===
Entrez le nom du fichier à lire :
inexistant.txt
Erreur lors de la lecture du fichier : inexistant.txt: openFile: does not exist (No such file or directory)
```

---

###  Remarque

Tu peux aussi utiliser cette approche avec d’autres opérations IO (écriture, suppression, etc.) :

```haskell
try (writeFile "test.txt" "Hello!") :: IO (Either IOException ())
