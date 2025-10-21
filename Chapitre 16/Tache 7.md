 HC16T7 : Vérification interactive de présence d’un élément

### code 
```haskell

import Text.Read (readMaybe)

-- Fonction qui vérifie si un élément est présent
elementDansListe :: Eq a => a -> [a] -> Bool
elementDansListe x xs = x `elem` xs

main :: IO ()
main = do
    putStrLn "=== Vérification de présence dans une liste ==="
    
    -- Lecture de la liste
    putStrLn "Entrez une liste d'entiers séparés par des espaces :"
    listeInput <- getLine
    let maybeListe = sequence (map readMaybe (words listeInput)) :: Maybe [Int]
    
    case maybeListe of
        Nothing -> putStrLn "Erreur : veuillez entrer uniquement des nombres entiers valides."
        Just liste -> do
            -- Lecture de l’élément à rechercher
            putStrLn "Entrez l'élément à rechercher :"
            elemInput <- getLine
            case readMaybe elemInput :: Maybe Int of
                Nothing -> putStrLn "Erreur : l’élément doit être un nombre entier."
                Just n  ->
                    if elementDansListe n liste
                        then putStrLn ("✅ " ++ show n ++ " est présent dans la liste.")
                        else putStrLn ("❌ " ++ show n ++ " n'est pas présent dans la liste.")
```

---

### Explications

1. **Lecture de la liste**

   * On lit une ligne de texte et on la découpe en mots (`words`).
   * `map readMaybe` convertit chaque mot en entier de manière sûre.
   * `sequence` transforme `[Maybe Int]` en `Maybe [Int]`.

2. **Gestion des erreurs**

   * Si la liste contient un élément non numérique → message d’erreur.
   * Si l’élément recherché n’est pas un entier → message d’erreur.

3. **Recherche**

   * Utilisation de `elementDansListe` pour vérifier la présence de l’élément.
   * Affichage du résultat avec un message clair.

---

###  Exemple d’exécution

✅ **Entrée valide :**

```
=== Vérification de présence dans une liste ===
Entrez une liste d'entiers séparés par des espaces :
3 5 7 10
Entrez l'élément à rechercher :
7
✅ 7 est présent dans la liste.
```

❌ **Liste invalide :**

```
Entrez une liste d'entiers séparés par des espaces :
3 5 a 10
Erreur : veuillez entrer uniquement des nombres entiers valides.
```

❌ **Élément invalide :**

```
Entrez une liste d'entiers séparés par des espaces :
1 2 3
Entrez l'élément à rechercher :
x
Erreur : l’élément doit être un nombre entier.
```
