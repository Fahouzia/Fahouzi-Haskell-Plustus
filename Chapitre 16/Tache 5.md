**HC16T5 : Mettre une chaîne en majuscules**

---

###  Objectif

Créer une fonction qui prend une **chaîne de caractères** et renvoie la même chaîne **tout en majuscules**.

---

###  Code

```haskell
-- HC16T5 : Mettre une chaîne en majuscules

import Data.Char (toUpper)

-- Fonction qui convertit une chaîne en majuscules
mettreEnMajuscules :: String -> String
mettreEnMajuscules s = map toUpper s

-- Programme principal pour tester
main :: IO ()
main = do
    putStrLn "Entrez une chaîne de caractères :"
    input <- getLine
    putStrLn ("Chaîne en majuscules : " ++ mettreEnMajuscules input)
```

---

###  Explications pas à pas

1. **Importation**

```haskell
import Data.Char (toUpper)
```

* `toUpper` est une fonction qui transforme un **caractère en majuscule**.

2. **Fonction `mettreEnMajuscules`**

```haskell
mettreEnMajuscules s = map toUpper s
```

* `map` applique `toUpper` à chaque caractère de la chaîne.

3. **Bloc `main`**

* Lit une chaîne avec `getLine`.
* Appelle `mettreEnMajuscules`.
* Affiche le résultat.

---

###  Exemple d’exécution

```
Entrez une chaîne de caractères :
bonjour tout le monde
Chaîne en majuscules : BONJOUR TOUT LE MONDE
```

---
