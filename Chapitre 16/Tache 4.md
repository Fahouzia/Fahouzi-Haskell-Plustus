**HC16T4 : Filtrer les nombres pairs**

---

###  Objectif

Écrire une fonction qui prend une liste d’entiers et renvoie une nouvelle liste contenant **uniquement les nombres pairs**.

---

###  Explication

En Haskell, on peut filtrer une liste avec la fonction standard `filter`, qui prend :

* une **fonction prédicat** (qui retourne `True` ou `False`),
* et une **liste** à filtrer.

Pour savoir si un nombre est pair, on utilise l’opérateur `even`.

---

###  Code 

```haskell
-- HC16T4 : Filtrer les nombres pairs

-- Fonction qui filtre les nombres pairs d'une liste
filtrerPairs :: [Int] -> [Int]
filtrerPairs xs = filter even xs

-- Fonction principale pour tester
main :: IO ()
main = do
    putStrLn "Entrez une liste de nombres séparés par des espaces :"
    input <- getLine
    let nombres = map read (words input) :: [Int]
    let pairs = filtrerPairs nombres
    putStrLn ("Les nombres pairs sont : " ++ show pairs)
```

---

###  Explication pas à pas

1. **`getLine`** lit la saisie de l’utilisateur (une ligne complète).
2. **`words`** découpe la chaîne en une liste de mots séparés par des espaces.
3. **`map read`** convertit chaque mot en entier (`Int`).
4. **`filter even xs`** garde seulement les entiers pairs.
5. **`show`** convertit la liste des pairs en chaîne de caractères pour l’affichage.

---

###  Exemple d’exécution

```
Entrez une liste de nombres séparés par des espaces :
10 3 5 8 12 7
Les nombres pairs sont : [10,8,12]
```

---
