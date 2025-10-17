**HC14T8 : Fonction de comptage de fréquence de caractères**.


###  **Objectif**

Implémenter :

```haskell
counts :: String -> [(Char, Int)]
```

Cette fonction doit :

* Prendre une chaîne (`String`).
* Compter combien de fois chaque caractère apparaît.
* Retourner une **liste de couples** `(caractère, fréquence)`.

---

###  **Explication pas à pas**

1. Trier la chaîne avec `sort` pour regrouper les caractères identiques.
2. Utiliser `group` pour former des sous-listes de caractères identiques.
3. Mapper chaque sous-liste vers un tuple `(caractère, longueur)`.

---

###  **Code complet**

```haskell
module Main where

import Data.List (sort, group)

-- Fonction de comptage des fréquences de caractères
counts :: String -> [(Char, Int)]
counts str = [(head g, length g) | g <- group (sort str)]

main :: IO ()
main = do
  putStrLn "Entrez une chaîne :"
  input <- getLine
  print (counts input)
```

---

###  **Exemple d’exécution**

#### Entrée :

```
Entrez une chaîne :
haskell
```

#### Sortie :

```haskell
[('a',1),('e',1),('h',1),('k',1),('l',2),('s',1)]
```

---

### **Explication du code**

* `sort str` trie la chaîne : `"haskell"` → `"aehklls"`
* `group` regroupe les caractères identiques contigus : `["a","e","h","k","ll","s"]`
* La compréhension de liste `[(head g, length g) | g <- ...]` extrait le caractère et le compte.

-
