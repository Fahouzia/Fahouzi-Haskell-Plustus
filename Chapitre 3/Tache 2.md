HC3T2 – Déterminer la note à partir d’un score avec des gardes (`guards`)


Créer une fonction `grade :: Int -> String` qui :

* Prend un **score entier** (`Int`)
* Retourne une **note** (`String`) selon le barème suivant :

| Score            | Note |
| ---------------- | ---- |
| 90 et plus       | "A"  |
| 80 à 89          | "B"  |
| 70 à 79          | "C"  |
| 60 à 69          | "D"  |
| en dessous de 60 | "F"  |

---

CODE 
```haskell
-- Fonction qui retourne la note en fonction du score
grade :: Int -> String
grade score
    | score >= 90 = "A"
    | score >= 80 = "B"
    | score >= 70 = "C"
    | score >= 60 = "D"
    | otherwise   = "F"

-- Fonction main pour tester
main :: IO ()
main = do
    print (grade 95)  -- Résultat : "A"
    print (grade 72)  -- Résultat : "C"
    print (grade 50)  -- Résultat : "F"
```

---

Explication

###  La signature

```haskell
grade :: Int -> String
```

* La fonction `grade` prend un `Int` (le score)
* Elle retourne un `String` (la note)

---

###  Les `guards`

```haskell
grade score
    | score >= 90 = "A"
    | score >= 80 = "B"
    | score >= 70 = "C"
    | score >= 60 = "D"
    | otherwise   = "F"
```

* Chaque `|` est une condition (appelée **garde**).
* La première condition vraie sera exécutée.
* `otherwise` signifie "dans tous les autres cas" (équivalent de `else`).
