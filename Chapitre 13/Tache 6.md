**HC13T6 : Convertir des fichiers filtrés en map**

---

## **Objectif**

Créer une fonction qui :

1. Prend une **liste de noms de fichiers filtrés** (par exemple, `["data.txt", "image.png", "report.pdf"]`),
2. Utilise le module `Data.Map` (alias `Map`),
3. Convertit cette liste en une **map (clé/valeur)**,

   * la **clé** est le nom du fichier,
   * la **valeur** est la **taille du nom** (ou tout autre attribut choisi).

---

##  **Code**

```haskell
-- HC13T6 : Convertir des fichiers filtrés en map
module HC13T6 where

import qualified Data.Map as Map

-- Fonction : convertir une liste de fichiers en une map (clé = nom, valeur = longueur du nom)
filesToMap :: [String] -> Map.Map String Int
filesToMap filenames = Map.fromList [(name, length name) | name <- filenames]

-- Exemple d'utilisation dans main
main :: IO ()
main = do
    putStrLn "=== HC13T6 : Conversion d'une liste de fichiers filtrés en Map ==="

    let filteredFiles = ["data.txt", "image.png", "report.pdf", "notes.md"]
    putStrLn "\nListe des fichiers filtrés :"
    print filteredFiles

    let fileMap = filesToMap filteredFiles
    putStrLn "\nConversion en Map (nom -> longueur du nom) :"
    print fileMap

    -- Exemple d’accès à une clé
    putStrLn "\nTaille du nom 'image.png' :"
    print (Map.lookup "image.png" fileMap)
```

---

##  **Explication détaillée**

### 1. **Importation du module**

```haskell
import qualified Data.Map as Map
```

 On importe le module `Data.Map` sous le nom court `Map` pour éviter les conflits avec d'autres fonctions `lookup` ou `insert`.

---

### 2. **Conversion de la liste en Map**

```haskell
filesToMap filenames = Map.fromList [(name, length name) | name <- filenames]
```

 Utilisation d’une **liste de paires clé/valeur** :
Chaque fichier devient `(nom, longueur)`, puis `Map.fromList` les transforme en dictionnaire.

Exemple :

```haskell
["data.txt", "report.pdf"] 
→ [("data.txt", 8), ("report.pdf", 10)]
→ Map.fromList [("data.txt", 8), ("report.pdf", 10)]
```

---

### 3. **Accès à une valeur**

```haskell
Map.lookup "image.png" fileMap
```

 Recherche de la valeur associée à la clé `"image.png"`.
Retourne :

* `Just 9` si la clé existe,
* `Nothing` sinon.

---

##  **Exemple d’exécution**

###  **Sortie console**

```
=== HC13T6 : Conversion d'une liste de fichiers filtrés en Map ===

Liste des fichiers filtrés :
["data.txt","image.png","report.pdf","notes.md"]

Conversion en Map (nom -> longueur du nom) :
fromList [("data.txt",8),("image.png",9),("notes.md",9),("report.pdf",10)]

Taille du nom 'image.png' :
Just 9
```

---

##  **Variante possible**

Tu peux modifier la valeur associée pour stocker :

* l’**extension du fichier** :

  ```haskell
  filesToMap filenames = Map.fromList [(name, takeExtension name) | name <- filenames]
  ```

  (en important `System.FilePath`)

* ou la **date de modification**, la **taille réelle**, etc., selon les besoins.
