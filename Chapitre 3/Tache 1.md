HC3T1 – Vérifier si un nombre est positif, négatif ou nul

CODE 

```haskell
-- Définition de la fonction avec if-then-else
checkNumber :: Int -> String
checkNumber n =
    if n > 0 then "Positif"
    else if n < 0 then "Négatif"
    else "Zéro"

-- Fonction main pour tester
main :: IO ()
main = do
    print (checkNumber 5)     -- Résultat : "Positif"
    print (checkNumber (-3))  -- Résultat : "Negatif"
    print (checkNumber 0)     -- Résultat : "Zero"
```

---

Explication

### 1. Signature

```haskell
checkNumber :: Int -> String
```

* La fonction prend un entier `n` et retourne une chaîne (`String`).

### 2. Structure `if-then-else`

```haskell
if n > 0 then "Positif"
else if n < 0 then "Négatif"
else "Zéro"
```

* Haskell **oblige à toujours avoir `else`**, car l’expression doit retourner **une seule valeur**.

### 3. Appels de test

```haskell
checkNumber 5     -- Positif
checkNumber (-3)  -- Négatif
checkNumber 0     -- Zéro
```

```haskell
checkNumber :: Int -> String
```

Cette fonction :

* Prend un entier (`Int`)
* Retourne un `String` :

  * `"Positif"` si le nombre > 0
  * `"Négatif"` si le nombre < 0
  * `"Zéro"` si le nombre == 0

---
