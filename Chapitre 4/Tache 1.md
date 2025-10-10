 HC4T1 - Définir une fonction weatherReport avec un main
 


```haskell
 -- Définition de la fonction weatherReport avec pattern matching
weatherReport :: String -> String
weatherReport "sunny"  = "It's a bright and beautiful day!"
weatherReport "rainy"  = "Don't forget your umbrella!"
weatherReport "cloudy" = "A bit gloomy, but no rain yet!"
weatherReport _        = "Weather unknown"  -- catch-all pour tout autre cas

-- Fonction main pour tester
main :: IO ()
main = do
    putStrLn (weatherReport "sunny")    -- Cas "sunny"
    putStrLn (weatherReport "rainy")    -- Cas "rainy"
    putStrLn (weatherReport "cloudy")   -- Cas "cloudy"
   

```
 Explication :

* `main :: IO ()` → point d’entrée du programme.
* `putStrLn` → affiche un message à l’écran.
* `getLine` → lit une entrée clavier (une chaîne).
* `putStrLn (weatherReport condition)` → affiche le message retourné par la fonction `weatherReport`.

weatherReport :: String -> String
→ La fonction prend une chaîne de caractères (comme "sunny") et retourne une autre chaîne de caractères (le message correspondant).

case condition of
→ C’est du pattern matching : on compare la valeur condition avec différents motifs.

"sunny", "rainy", "cloudy"
→ Chaque cas correspond à un motif précis.

_
→ Le caractère underscore signifie "tout autre cas" (valeur non reconnue).
 Exemple 

```
Entrez la condition météo (sunny, rainy, cloudy) :
sunny
Il fait beau et ensoleillé !
```
