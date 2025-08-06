HC2T5 - Tâche 5 : Définir et utiliser des fonctions


CODE
```haskell
-- Fonction qui calcule l'aire d'un cercle à partir du rayon (Float)
circleArea :: Float -> Float
circleArea r = pi * r * r

-- Fonction qui retourne le maximum parmi trois Int
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree x y z = max x (max y z)

-- Fonction main pour tester les deux fonctions
main :: IO ()
main = do
    -- Tests de circleArea
    print (circleArea 3.0)     -- Aire du cercle de rayon 3
    print (circleArea 5.5)     -- Aire du cercle de rayon 5.5

    -- Tests de maxOfThree
    print (maxOfThree 10 20 15)  -- Doit afficher 20
    print (maxOfThree 5 3 8)     -- Doit afficher 8
    print (maxOfThree (-1) (-5) 0) -- Doit afficher 0
```

---
EXPLICATION 

### 1. `circleArea`

* Signature : `Float -> Float`
  Elle prend un `Float` en entrée (le rayon) et retourne un `Float` (l’aire).
* Formule : `π * r²`
  On utilise la constante `pi` fournie par Haskell.

---

### 2. `maxOfThree`

* Signature : `Int -> Int -> Int -> Int`
  Trois entiers en entrée, un entier en sortie.
* Implémentation :
  On utilise la fonction `max` deux fois pour comparer les trois valeurs.

---

### 3. `main`

* Teste les fonctions avec différents exemples.
* Affiche les résultats dans la console.
