HC13T7 : Somme d'une liste avec module intégré

---

##  **Objectif**

1. Réutiliser le module **`SumNonEmpty`** que nous avons créé (ex. HC13T4/HC13T5).
2. Importer sa fonction `sumNonEmpty` dans **`Main.hs`**.
3. Calculer la somme d’une liste de nombres et l’afficher.

 code 
```haskell
-- HC13T7 : Somme d'une liste avec module intégré

-- Définition du module SumNonEmpty (interne)
module SumNonEmpty
( sumNonEmpty ) where

sumNonEmpty :: (Num a, Show a) => [a] -> a
sumNonEmpty [] = error errorMessage
sumNonEmpty xs = sum xs

-- Fonction interne non exportée
errorMessage :: String
errorMessage = "Erreur : la liste est vide ! Impossible de calculer la somme."

-- Fin du module SumNonEmpty

-- Programme principal
main :: IO ()
main = do
    putStrLn "=== HC13T7 : Test du module SumNonEmpty ==="

    -- Exemple 1 : liste non vide
    let numbers = [5, 10, 15, 20]
    putStrLn ("Liste : " ++ show numbers)
    putStrLn ("Somme : " ++ show (SumNonEmpty.sumNonEmpty numbers))

    -- Exemple 2 : liste vide pour démontrer l'erreur
    putStrLn "\nTest avec une liste vide :"
    print (SumNonEmpty.sumNonEmpty [])
```

---

###  **Explication **

* Le module `SumNonEmpty` est **déclaré en début de fichier** et contient la fonction `sumNonEmpty`.
* Dans `main`, on **appelle la fonction via `SumNonEmpty.sumNonEmpty`**.
* La fonction renvoie **une erreur explicite** si la liste est vide.

---

1. **Import du module**

```haskell
import SumNonEmpty
```

 Seule la fonction `sumNonEmpty` est accessible depuis `Main.hs`.

2. **Calcul de la somme**

```haskell
sumNonEmpty numbers
```

* Calcule la somme des éléments de la liste `numbers`.
* Si la liste est vide, l’erreur interne du module est affichée.

3. **Affichage**

```haskell
putStrLn ("Somme : " ++ show (sumNonEmpty numbers))
```

* Convertit le résultat en chaîne pour l’affichage.

---

##  **Exemple d’exécution**

###  Cas liste non vide

```
=== HC13T7 : Test du module SumNonEmpty ===
Liste : [5,10,15,20]
Somme : 50
```

###  Cas liste vide

```
Test avec une liste vide :
Erreur : la liste est vide ! Impossible de calculer la somme.
```

---
