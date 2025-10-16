**HC13T4 : Module SumNonEmpty**

---

###  **Objectif**

Créer un **module Haskell** nommé `SumNonEmpty` qui :

1. Définit une fonction `sumNonEmpty`,
2. Calcule la **somme des éléments d’une liste**,
3. Retourne une **erreur explicite** si la liste est vide,
4. Et montrer son **utilisation dans un fichier `Main.hs`**.

---


###  *CODE *

```haskell
-- HC13T4 : Module SumNonEmpty
module SumNonEmpty
( sumNonEmpty ) where

-- Fonction qui calcule la somme d'une liste non vide
sumNonEmpty :: (Num a, Show a) => [a] -> a
sumNonEmpty [] = error "Erreur : la liste est vide ! Impossible de calculer la somme."
sumNonEmpty xs = sum xs
-- Programme principal pour tester le module SumNonEmpty
import SumNonEmpty

main :: IO ()
main = do
    putStrLn "=== Test du module SumNonEmpty ==="

    -- Exemple 1 : liste non vide
    let liste1 = [1, 2, 3, 4, 5]
    putStrLn ("Somme de " ++ show liste1 ++ " = " ++ show (sumNonEmpty liste1))

    -- Exemple 2 : liste vide
    putStrLn "\nTentative avec une liste vide..."
    print (sumNonEmpty [])
```

---

###  **Explication pas à pas**

####  Module `SumNonEmpty.hs`

* `module SumNonEmpty (sumNonEmpty) where`
  → Définit le nom du module et **exporte uniquement** la fonction `sumNonEmpty`.

* `sumNonEmpty :: (Num a, Show a) => [a] -> a`
  → La fonction prend une **liste de nombres** et renvoie un **nombre**.

* `sumNonEmpty [] = error "Erreur : la liste est vide !..."`
  → Si la liste est vide, on déclenche une **erreur explicite** avec un message clair.

* `sumNonEmpty xs = sum xs`
  → Sinon, on calcule la somme normalement avec la fonction standard `sum`.

####  Fichier `Main.hs`

* On **importe** le module `SumNonEmpty`.
* On teste la fonction avec une liste normale et une liste vide.

---

###  **Exemple d’exécution**

####  Cas normal :

```
=== Test du module SumNonEmpty ===
Somme de [1,2,3,4,5] = 15
```

####  Cas d’erreur (liste vide) :

```
Tentative avec une liste vide...
Erreur : la liste est vide ! Impossible de calculer la somme.
```

*(Le programme s’arrête après l’erreur, car `error` interrompt l’exécution.)*
