 HC4T1 - Définir une fonction weatherReport avec un main

```haskell

weatherReport :: String -> String
weatherReport condition = case condition of
    "sunny"  -> "Il fait beau et ensoleillé !"
    "rainy"  -> "N'oublie pas ton parapluie !"
    "cloudy" -> "Un peu gris, mais pas de pluie pour l'instant !"
    _        -> "Météo inconnue"

main :: IO ()
main = do
    putStrLn "Entrez la condition météo (sunny, rainy, cloudy) :"
    condition <- getLine
    putStrLn (weatherReport condition)
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
