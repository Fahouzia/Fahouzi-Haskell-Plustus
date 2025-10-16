HC11T10 : Fonction sortContainers

## 🔹 Énoncé

> Implémenter une fonction `sortContainers` qui trie une liste de containers à l’aide de l’instance `Ord` dérivée.

---

## 🔹 Code complet (copiable)

```haskell
import Data.List (sort)

-- Définition du type Box (notre container)
data Box a = Empty | Has a
  deriving (Show, Eq, Ord)

-- Fonction pour trier une liste de containers (Box)
sortContainers :: (Ord a) => [Box a] -> [Box a]
sortContainers = sort

-- Programme principal pour tester
main :: IO ()
main = do
  let boxes = [Has 10, Empty, Has 5, Has 20, Empty, Has 15]
  
  putStrLn "Liste de départ :"
  print boxes
  
  let sorted = sortContainers boxes
  putStrLn "\nListe triée :"
  print sorted
```

---

## 🔹 Explication pas à pas

1. **Import de `Data.List` :**

   ```haskell
   import Data.List (sort)
   ```

   → La fonction `sort` trie des listes, mais elle nécessite que les éléments appartiennent à une classe `Ord`.

2. **Définition du type `Box` :**

   ```haskell
   data Box a = Empty | Has a
     deriving (Show, Eq, Ord)
   ```

   * `Eq` → permet de comparer l’égalité (`==`).
   * `Ord` → permet de comparer l’ordre (`<`, `>`, etc.), indispensable pour le tri.

   🔹 L’ordre dérivé est automatique :

   ```
   Empty < Has x   (pour toute valeur x)
   Et Has x < Has y si x < y
   ```

3. **Définition de `sortContainers` :**

   ```haskell
   sortContainers :: (Ord a) => [Box a] -> [Box a]
   sortContainers = sort
   ```

   → Cette fonction trie simplement la liste en utilisant `sort`.
   → On garde les `Empty` d’abord, puis les `Has` triés selon la valeur.

4. **Test dans `main` :**
   On crée une liste mélangée :

   ```haskell
   [Has 10, Empty, Has 5, Has 20, Empty, Has 15]
   ```

   Puis on la trie avec `sortContainers`.

---

## 🔹 Exemple de sortie

```
Liste de départ :
[Has 10,Empty,Has 5,Has 20,Empty,Has 15]

Liste triée :
[Empty,Empty,Has 5,Has 10,Has 15,Has 20]
```

---

## 🔹 En résumé

* On a dérivé `Ord` pour `Box` → tri automatique.
* La fonction `sortContainers` réutilise simplement la fonction standard `sort`.
* L’ordre par défaut place les boîtes vides avant les pleines, puis trie les valeurs internes.

---
