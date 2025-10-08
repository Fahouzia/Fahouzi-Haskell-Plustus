**HC7T5 – Fonction utilisant la contrainte `Num`**

---

##  Objectif

* Créer une fonction `squareArea` qui prend **la longueur d’un côté** et retourne **l’aire du carré**.
* La fonction doit être **générique pour tout type numérique** (`Int`, `Float`, `Double`, etc.).

---

##  Code 
```haskell
-- HC7T5 : Fonction utilisant la contrainte Num

-- Définition de la fonction squareArea
squareArea :: Num a => a -> a
squareArea side = side * side

-- Fonction principale main pour tester
main :: IO ()
main = do
    let sideInt = 5 :: Int
    let sideFloat = 3.5 :: Float

    putStrLn ("Aire d'un carré côté " ++ show sideInt ++ " : " ++ show (squareArea sideInt))
    putStrLn ("Aire d'un carré côté " ++ show sideFloat ++ " : " ++ show (squareArea sideFloat))
```

---

##  Explication pas à pas

### 1️⃣ Signature de la fonction

```haskell
squareArea :: Num a => a -> a
```

* `Num a =>` → **contrainte de type** : `a` doit être un type numérique

  * Permet d’utiliser `*` et `+` sur ce type
* `a -> a` → prend une valeur numérique et retourne une valeur numérique du même type

---

### 2️⃣ Définition de la fonction

```haskell
squareArea side = side * side
```

* Aire d’un carré = côté × côté
* `*` fonctionne pour tout type `Num` (`Int`, `Float`, `Double`, etc.)

---

### 3️⃣ Fonction `main` (tests)

```haskell
main :: IO ()
main = do
    let sideInt = 5 :: Int
    let sideFloat = 3.5 :: Float

    putStrLn ("Aire d'un carré côté " ++ show sideInt ++ " : " ++ show (squareArea sideInt))
    putStrLn ("Aire d'un carré côté " ++ show sideFloat ++ " : " ++ show (squareArea sideFloat))
```

* On teste avec un entier (`Int`)
* On teste avec un nombre flottant (`Float`)
* `show` convertit les nombres en texte pour affichage

---

###  Exemple de sortie

```
Aire d'un carré côté 5 : 25
Aire d'un carré côté 3.5 : 12.25
```

---

 **Remarque**

* La **contrainte `Num`** rend la fonction **générique pour tout type numérique**
* Si on voulait inclure les nombres flottants pour les fonctions trigonométriques, on pourrait utiliser `Floating a => a -> a`.

---

Veux‑tu que je fasse ça ?
