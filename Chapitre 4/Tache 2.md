HC4T2 - Définir une fonction dayType avec un main

```haskell
-- 
dayType :: String -> String
dayType day = case day of
    "Saturday" -> "C'est le week-end !"
    "Sunday"   -> "C'est le week-end !"
    "Monday"   -> "C'est un jour de semaine."
    "Tuesday"  -> "C'est un jour de semaine."
    "Wednesday"-> "C'est un jour de semaine."
    "Thursday" -> "C'est un jour de semaine."
    "Friday"   -> "C'est un jour de semaine."
    _          -> "Jour invalide"

main :: IO ()
main = do
    putStrLn "Entrez un jour de la semaine (ex: Monday, Tuesday, ...):"
    day <- getLine
    putStrLn (dayType day)
```

## Explication :

* `dayType :: String -> String` → la fonction prend une chaîne (le nom du jour) et retourne une phrase descriptive.
* `case day of` → compare le jour entré à différents cas possibles.
* `_` → correspond à tous les autres cas (ici, les entrées invalides).

Exemple

```
Entrez un jour de la semaine (ex: Monday, Tuesday, ...):
Saturday
C'est le week-end !
```
