HC13T9 : Renommer un espace de noms de module

---

## **Objectif**

1. Montrer un conflit de noms entre deux modules (par exemple `Data.Map` et `Data.Set` qui ont des fonctions similaires).
2. Résoudre ce conflit en utilisant **des importations qualifiées** (`qualified`).
3. Appeler les fonctions en précisant le **préfixe du module**.

---

##  **Code **

```haskell
-- Import de Data.List avec alias L
import qualified Data.List as L
-- Import de System.Directory avec alias D
import qualified System.Directory as D

main :: IO ()
main = do
    putStrLn "=== HC13T9 : Renaming Module Namespace ==="

    -- Utilisation d'une fonction de Data.List (alias L)
    let liste = [5, 2, 9, 1, 7]
    putStrLn ("Liste originale : " ++ show liste)
    putStrLn ("Liste triée avec L.sort : " ++ show (L.sort liste))

    -- Utilisation d'une fonction de System.Directory (alias D)
    putStrLn "\nFichiers dans le répertoire courant :"
    fichiers <- D.getDirectoryContents "."
    putStrLn ("Tous les fichiers : " ++ show fichiers)

    -- Filtrage des fichiers contenant ".hs" avec L.filter
    let fichiersHs = L.filter (L.isInfixOf ".hs") fichiers
    putStrLn ("Fichiers Haskell (.hs) : " ++ show fichiersHs)

```

---

##  **Explication pas à pas**

1. **Importations qualifiées**

```haskell
import qualified Data.Map as Map
import qualified Data.Set as Set
```

 On ajoute un **préfixe** (`Map` ou `Set`) pour **éviter les conflits de noms**.

* Sans préfixe, des fonctions comme `lookup` ou `member` pourraient entrer en conflit.

2. **Utilisation des fonctions avec préfixe**

```haskell
Map.fromList [...]
Map.lookup "Alice" myMap

Set.fromList [...]
Set.member 3 mySet
```

Chaque fonction est appelée avec son **module qualifié**.

3. **Résultat lisible et clair**

* `myMap` et `mySet` peuvent avoir des fonctions de noms similaires sans créer d’ambiguïté.

---

## **Exemple d’exécution**

```
=== HC13T8 : Importations qualifiées ===

Contenu de la Map :
fromList [("Alice",25),("Bob",30)]
Valeur associée à 'Alice' : Just 25

Contenu du Set :
fromList [1,2,3,4,5]
Le nombre 3 est-il dans le Set ? True
```

---
