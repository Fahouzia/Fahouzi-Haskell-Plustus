HC3T5 - Tâche 5 : Déterminer le type d’un triangle avec des gardes

```haskell
-- HC3T5 - Déterminer le type d’un triangle avec des gardes

triangleType :: Float -> Float -> Float -> String
triangleType a b c
  | a == b && b == c = "Équilatéral"
  | a == b || b == c || a == c = "Isocèle"
  | otherwise = "Scalène"

-- Tests
main :: IO ()
main = do
  print (triangleType 3 3 3)   -- "Équilatéral"
  print (triangleType 5 5 8)   -- "Isocèle"
  print (triangleType 6 7 8)   -- "Scalène"
```

---

Explication :

* La fonction `triangleType` reçoit 3 côtés `a`, `b`, `c`.
* Elle utilise des **gardes (`|`)** pour tester les conditions :

  * Tous égaux → `Équilatéral`
  * Deux égaux → `Isocèle`
  * Aucun égal → `Scalène`
* La fonction `main` permet de tester directement le programme avec quelques exemples.

---
