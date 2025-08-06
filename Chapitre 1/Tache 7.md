HC1T7 - Tâche 7 : Conversion Fahrenheit/Celsius

CODE 
```haskell
-- Définition de la fonction de conversion Fahrenheit → Celsius
fToC :: Float -> Float
fToC f = (f - 32) * (5 / 9)

-- Exemple d’utilisation dans main
main :: IO ()
main = do
    print (fToC 32)   -- Résultat attendu : 0.0
    print (fToC 212)  -- Résultat attendu : 100.0
```

EXPLICATION

### 1. Signature de type

```haskell
fToC :: Float -> Float
```

* `fToC` est le **nom de la fonction**.
* `::` indique la **signature de type**.
* `Float -> Float` signifie :

  * La fonction prend une valeur `Float` (par exemple `32.0`).
  * Elle retourne un résultat de type `Float`.

### 2. Corps de la fonction

```haskell
fToC f = (f - 32) * (5 / 9)


* `f` est l’**entrée** (la température en Fahrenheit).
* `(f - 32)` : on soustrait 32 comme dans la formule standard.
* `(5 / 9)` : fraction exacte pour convertir l’échelle.
* `*` : multiplication.
* Résultat : température convertie en Celsius.


### 3. Fonction `main`
En Haskell, main est le point d'entrée du programme — c’est la première fonction exécutée quand tu lances ton code compilé ou ton script.




