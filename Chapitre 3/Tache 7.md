 HC3T7 : Déterminer la saison en fonction du mois avec des gardes
code
```haskell
-- HC3T7 : Déterminer la saison en fonction du mois avec des gardes

season :: Int -> String
season month
    | month == 12 || month == 1 || month == 2  = "Hiver"
    | month == 3  || month == 4 || month == 5  = "Printemps"
    | month == 6  || month == 7 || month == 8  = "Été"
    | month == 9  || month == 10 || month == 11 = "Automne"
    | otherwise = "Mois invalide"

main :: IO ()
main = do
    putStrLn ("season 3  → " ++ season 3)
    putStrLn ("season 7  → " ++ season 7)
    putStrLn ("season 11 → " ++ season 11)
```

---

resutat:

```
season 3  → Printemps
season 7  → Été
season 11 → Automne
```
EXPICATION 

1. La signature de la fonction

```haskell
season :: Int -> String
```

Cela signifie que la fonction `season` prend un **entier (`Int`)** en entrée (le mois)
et renvoie une **chaîne de caractères (`String`)** correspondant à la saison.

Exemple :
`season 3` → renvoie `"Printemps"`

---

 2. Les gardes (`|`)

```haskell
season month
    | month == 12 || month == 1 || month == 2  = "Hiver"
```

On appelle ça des **gardes** (guards) en Haskell :
Elles permettent de tester plusieurs conditions **dans l’ordre**.

Ici :

* Si le mois est 12, 1 ou 2 → on retourne `"Hiver"`.
* Sinon, on continue à tester les autres gardes.

---

3. Les autres gardes

```haskell
    | month == 3  || month == 4 || month == 5  = "Printemps"
    | month == 6  || month == 7 || month == 8  = "Été"
    | month == 9  || month == 10 || month == 11 = "Automne"
```

Chaque ligne correspond à une saison selon le mois.

---

4. Le cas par défaut : `otherwise`

```haskell
    | otherwise = "Mois invalide"
```

 `otherwise` agit comme **le "sinon"** (équivalent à `else`).
Si le mois ne correspond à aucune des conditions précédentes (par exemple `13` ou `0`),
on renvoie `"Mois invalide"`.

---

5. Le `main`

```haskell
main :: IO ()
main = do
    putStrLn ("season 3  → " ++ season 3)
    putStrLn ("season 7  → " ++ season 7)
    putStrLn ("season 11 → " ++ season 11)
```

`main` est le **point d’entrée du programme** (comme en Java ou C).

* `putStrLn` affiche du texte à l’écran.
* `"season 3  → " ++ season 3` signifie qu’on **concatène** (avec `++`) du texte et le résultat de la fonction `season`.

🧾 En résumé :

* `season 3` renvoie `"Printemps"`
* `season 7` renvoie `"Été"`
* `season 11` renvoie `"Automne"`


