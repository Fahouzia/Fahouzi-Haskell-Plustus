**HC7T6 – Utiliser `Integral` et `Floating`**
---

##  Objectif

* Créer une fonction `circleCircumference` qui prend **un rayon** et retourne **la circonférence** d’un cercle.
* Elle doit fonctionner avec :

  * **types intégral** (`Int`, `Integer`)
  * **types flottants** (`Float`, `Double`)

---

##  Code 

```haskell
-- HC7T6 : Fonction circleCircumference avec Integral et Floating

-- Définition de la fonction
circleCircumference :: (Integral a, Floating b) => a -> b
circleCircumference r = 2 * pi * fromIntegral r
-- fromIntegral convertit un nombre intégral en type flottant

-- Fonction principale main pour tester
main :: IO ()
main = do
    let radiusInt = 5 :: Int
    let radiusInteger = 7 :: Integer
    let radiusFloat = 3.5 :: Float

    putStrLn ("Circonférence cercle rayon " ++ show radiusInt ++ " : " ++ show (circleCircumference radiusInt))
    putStrLn ("Circonférence cercle rayon " ++ show radiusInteger ++ " : " ++ show (circleCircumference radiusInteger))
    putStrLn ("Circonférence cercle rayon " ++ show radiusFloat ++ " : " ++ show (circleCircumference (round radiusFloat)))
```

---

##  Explication pas à pas

### 1️⃣ Signature de la fonction

```haskell
circleCircumference :: (Integral a, Floating b) => a -> b
```

* `(Integral a, Floating b)` → contraintes multiples :

  * `a` : type **entier** (`Int`, `Integer`) pour le rayon
  * `b` : type **flottant** (`Float`, `Double`) pour le résultat
* `a -> b` → prend un entier et retourne un nombre flottant

---

### 2️⃣ Définition de la fonction

```haskell
circleCircumference r = 2 * pi * fromIntegral r
```

* `2 * pi * r` → formule de la circonférence
* `fromIntegral r` → convertit le type intégral `r` en type flottant, car `pi` est de type `Floating`

---

### 3️⃣ Fonction `main` (tests)

* Test avec un **Int** : 5 → résultat en `Double`
* Test avec un **Integer** : 7 → résultat en `Double`
* Test avec un **Float** : 3.5 → on utilise `round` pour convertir en `Int`

```haskell
show` convertit le résultat en texte pour l’affichage
```

---

### 4️⃣ Exemple de sortie

```
Circonférence cercle rayon 5 : 31.41592653589793
Circonférence cercle rayon 7 : 43.982297150257104
Circonférence cercle rayon 3.5 : 21.991148575128552
```

---

 **Remarque**

* `fromIntegral` est **très important** pour convertir un nombre entier en flottant, sinon Haskell génère une erreur de type
* Cette fonction est **générique** pour tout type entier (`Int`, `Integer`) et retourne un résultat flottant précis (`Float`, `Double`)

---

Veux‑tu que je fasse ça ?
