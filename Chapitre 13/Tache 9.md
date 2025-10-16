HC13T9 : Renommer un espace de noms de module

---

## **Objectif**

1. Montrer un conflit de noms entre deux modules (par exemple `Data.Map` et `Data.Set` qui ont des fonctions similaires).
2. Résoudre ce conflit en utilisant **des importations qualifiées** (`qualified`).
3. Appeler les fonctions en précisant le **préfixe du module**.

---

##  **Code **

```haskell
-- HC13T8 : Gestion des conflits de noms avec importations qualifiées

-- Importations qualifiées
import qualified Data.Map as Map   -- Map est utilisé avec le préfixe Map
import qualified Data.Set as Set   -- Set est utilisé avec le préfixe Set

main :: IO ()
main = do
    putStrLn "=== HC13T8 : Importations qualifiées ==="

    -- Exemple avec Data.Map
    let myMap = Map.fromList [("Alice", 25), ("Bob", 30)]
    putStrLn "\nContenu de la Map :"
    print myMap

    -- Recherche dans la Map
    putStrLn ("Valeur associée à 'Alice' : " ++ show (Map.lookup "Alice" myMap))

    -- Exemple avec Data.Set
    let mySet = Set.fromList [1,2,3,4,5]
    putStrLn "\nContenu du Set :"
    print mySet

    -- Vérification de présence dans le Set
    putStrLn ("Le nombre 3 est-il dans le Set ? " ++ show (Set.member 3 mySet))
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
