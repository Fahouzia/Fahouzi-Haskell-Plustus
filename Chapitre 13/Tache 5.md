**HC13T5 : Restreindre la visibilité dans le module**
---

##  **Objectif**

Refactoriser le module `SumNonEmpty` pour :

1. Conserver la fonction principale `sumNonEmpty`,
2. Créer une **fonction utilitaire interne** (par ex. `errorMessage`) **non exportée**,
3. S’assurer que **seule** `sumNonEmpty` soit accessible à l’extérieur du module.

---



---

##  **CODE **

```haskell
-- Programme principal pour tester le module SumNonEmpty
-- HC13T5 : Restreindre la visibilité dans le module
module SumNonEmpty
( sumNonEmpty ) where

-- Fonction principale exportée
sumNonEmpty :: (Num a, Show a) => [a] -> a
sumNonEmpty [] = error errorMessage
sumNonEmpty xs = sum xs

-- Fonction utilitaire interne (non exportée)
errorMessage :: String
errorMessage = "Erreur : la liste est vide ! Impossible de calculer la somme."
import SumNonEmpty

main :: IO ()
main = do
    putStrLn "=== Test du module SumNonEmpty (avec visibilité restreinte) ==="

    -- Exemple 1 : liste non vide
    let liste1 = [10, 20, 30]
    putStrLn ("Somme de " ++ show liste1 ++ " = " ++ show (sumNonEmpty liste1))

    -- Exemple 2 : liste vide
    putStrLn "\nTentative avec une liste vide..."
    print (sumNonEmpty [])
```

---

##  **Explication pas à pas**

### 1. **Exportation limitée**

```haskell
module SumNonEmpty
( sumNonEmpty ) where
```

 Seule la fonction `sumNonEmpty` est **exportée**.
Les autres définitions (comme `errorMessage`) **ne sont pas visibles** en dehors du module.

### 2. **Utilisation d’une fonction interne**

```haskell
errorMessage :: String
errorMessage = "Erreur : la liste est vide ! Impossible de calculer la somme."
```

 Cette fonction est **internement utilisée** par `sumNonEmpty`, mais **non accessible** dans `Main.hs`.

### 3. **Protection de l’interface du module**

L’utilisateur du module ne peut **appeler que `sumNonEmpty`**.
S’il essaie de faire :

```haskell
import SumNonEmpty
main = putStrLn errorMessage
```

 GHC affichera :

```
Not in scope: ‘errorMessage’
```

 Cela prouve que la fonction interne est bien **cachée**.

---

##  **Exemple d’exécution**

###  Cas normal :

```
=== Test du module SumNonEmpty (avec visibilité restreinte) ===
Somme de [10,20,30] = 60
```

###  Cas d’erreur :

```
Tentative avec une liste vide...
Erreur : la liste est vide ! Impossible de calculer la somme.
```

---

##  **Résumé**

| Élément        | Exporté ? | Rôle                           |
| -------------- | --------- | ------------------------------ |
| `sumNonEmpty`  |  Oui     | Fonction principale (publique) |
| `errorMessage` |  Non     | Fonction interne (privée)      |

-
