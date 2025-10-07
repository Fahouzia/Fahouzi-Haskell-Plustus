HC3T8 : Calculer l’IMC et retourner la catégorie avec where

```haskell

bmiCategory :: Float -> Float -> String
bmiCategory poids taille
    | bmi < 18.5  = "Insuffisance pondérale"
    | bmi < 25    = "Normal"
    | bmi < 30    = "Surpoids"
    | otherwise   = "Obésité"
    where bmi = poids / (taille ^ 2)

main :: IO ()
main = do
    putStrLn ("bmiCategory 70 1.75 → " ++ bmiCategory 70 1.75)
    putStrLn ("bmiCategory 90 1.8  → " ++ bmiCategory 90 1.8)
```

---
RESULTAT 
```
bmiCategory 70 1.75 → Normal
bmiCategory 90 1.8  → Surpoids
```

---

**Explication détaillée**

###1. Signature de la fonction

```haskell
bmiCategory :: Float -> Float -> String
```

La fonction prend deux nombres à virgule flottante :

* le **poids (en kg)**,
* la **taille (en mètres)**,
  et renvoie une **chaîne de caractères** correspondant à la catégorie IMC.

---

###  2. Utilisation de `where`

```haskell
where bmi = poids / (taille ^ 2)
```

 `where` permet de **définir une variable locale** à la fonction.
Ici on calcule :
[
\text{bmi} = \frac{\text{poids}}{\text{taille}^2}
]

C’est l’**Indice de Masse Corporelle (IMC)**.

---

###  3. Les gardes (`|`)

```haskell
    | bmi < 18.5  = "Insuffisance pondérale"
    | bmi < 25    = "Normal"
    | bmi < 30    = "Surpoids"
    | otherwise   = "Obésité"
```

Ces conditions classifient la personne selon son IMC :

| Intervalle IMC | Catégorie              |
| -------------- | ---------------------- |
| < 18.5         | Insuffisance pondérale |
| 18.5 – 24.9    | Normal                 |
| 25 – 29.9      | Surpoids               |
| ≥ 30           | Obésité                |

Le mot-clé **`otherwise`** signifie "sinon" (comme `else`).

---

###  4. Fonction `main`

```haskell
main :: IO ()
main = do
    putStrLn ("bmiCategory 70 1.75 → " ++ bmiCategory 70 1.75)
    putStrLn ("bmiCategory 90 1.8  → " ++ bmiCategory 90 1.8)
```

C’est le **point d’entrée du programme**.
Il affiche le résultat de la fonction avec deux exemples.
