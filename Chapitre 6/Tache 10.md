HC6T10 : Récupérer les chiffres d'un nombre (récursif)


##  Objectif

Créer une fonction `digits` qui prend un **nombre entier positif** et retourne **une liste contenant chacun de ses chiffres**.

Exemple :

```
digits 12345 → [1,2,3,4,5]
```

---

##  Code complet (copiable)

```haskell
-- HC6T10 : Récupérer les chiffres d'un nombre (récursif)

-- Définition de la fonction digits
digits :: Int -> [Int]
digits n
    | n < 10    = [n]           -- Cas de base : un chiffre → liste contenant ce chiffre
    | otherwise = digits (n `div` 10) ++ [n `mod` 10]  -- Diviser et ajouter le dernier chiffre

-- Fonction principale main pour tester
main :: IO ()
main = do
    let nombre = 12345
    let resultat = digits nombre
    putStrLn ("Nombre : " ++ show nombre)
    putStrLn ("Liste des chiffres : " ++ show resultat)
```

---

##  Explication pas à pas

### 1️ Signature de la fonction

```haskell
digits :: Int -> [Int]
```

* `Int` → nombre entier d’entrée
* `[Int]` → liste de chiffres en sortie

---

### 2️ Cas de base

```haskell
| n < 10 = [n]
```

* Si le nombre est **un seul chiffre**, on renvoie une **liste contenant ce chiffre**.
* Exemple : `digits 7 → [7]`

---

### 3️⃣ Cas récursif

```haskell
| otherwise = digits (n `div` 10) ++ [n `mod` 10]
```

* `n `div` 10` → supprime le dernier chiffre du nombre

  * Exemple : `12345 div 10 → 1234`
* `n `mod` 10` → récupère le **dernier chiffre**

  * Exemple : `12345 mod 10 → 5`
* `++ [n mod 10]` → ajoute le dernier chiffre à la fin de la liste obtenue par la récursion

---

### 4️⃣ Exemple de déroulement

Nombre : `123`

```
digits 123
→ digits 12 ++ [3]
→ (digits 1 ++ [2]) ++ [3]
→ ([1] ++ [2]) ++ [3]
→ [1,2] ++ [3]
→ [1,2,3]
```


---

### 5️⃣ Fonction `main`

* On définit `nombre = 12345`
* On appelle `digits nombre` pour obtenir la liste des chiffres
* On affiche le nombre et la liste

###  Exemple de sortie

```
Nombre : 12345
Liste des chiffres : [1,2,3,4,5]
```

---
