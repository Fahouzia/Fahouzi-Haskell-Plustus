HC3T3 - Tâche 3 : Convertir une couleur RGB en chaîne hexadécimale avec let

```haskell
rgbToHex :: (Int, Int, Int) -> String
```
cette fonction qui transforme, par exemple :

```haskell
rgbToHex (255, 0, 127)
```
en
`"#FF007F"`

---
 Étape 1 : Comprendre la conversion

Chaque composant (R, G, B) est un entier entre **0 et 255**.
On veut le convertir en **hexadécimal à deux chiffres** :

* 255 → "FF"
* 0 → "00"
* 127 → "7F"

---

Étape 2 : Utiliser `Numeric.showHex`

Le module `Numeric` contient une fonction `showHex` qui convertit un entier en hexadécimal.
👉 Il faut l’importer :

```haskell
import Numeric (showHex)
```

---

Étape 3 : Construire la fonction avec `let`

```haskell
import Numeric (showHex)
import Data.Char (toUpper)

rgbToHex :: (Int, Int, Int) -> String
rgbToHex (r, g, b) =
  let
    -- Fonction locale pour formater chaque valeur sur 2 caractères
    toHex n = let h = showHex n ""
              in if length h == 1 then '0' : map toUpper h else map toUpper h
    -- Conversion de chaque composant
    rHex = toHex r
    gHex = toHex g
    bHex = toHex b
  in
    '#' : rHex ++ gHex ++ bHex
```

---

Étape 4 : Tests

```haskell
main = do
  print (rgbToHex (255, 0, 127))   -- "#FF007F"
  print (rgbToHex (0, 255, 64))    -- "#00FF40"
```

---
Explication :

* `let ... in ...` : permet de définir des **valeurs locales**.
* `showHex n ""` : convertit le nombre `n` en chaîne hexadécimale.
* `if length h == 1 then '0' : h` : ajoute un `0` si le résultat n’a qu’un caractère.
* `map toUpper` : met les lettres en majuscules (pour obtenir `FF` au lieu de `ff`).
* `'#' : ...` : ajoute le `#` au début de la chaîne finale.

