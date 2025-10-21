
HC15T7 : Calcul de vitesse avec gestion des valeurs optionnelles et du parsing** �

---

###  Objectif

Écrire un programme Haskell qui :

1. Demande à l’utilisateur une **distance (en km)** et un **temps (en h)**,
2. Utilise `readMaybe` pour parser les deux valeurs de manière sûre,
3. Utilise `Maybe` pour éviter la division par zéro,
4. Calcule la **vitesse = distance / temps** si tout est valide,
5. Affiche des messages clairs en cas d’erreur.

---

###  Code 
```haskell
-- HC15T7 : Calcul de vitesse avec gestion des valeurs optionnelles et du parsing

import Text.Read (readMaybe)

-- Fonction de division sécurisée
safeDivide :: Double -> Double -> Maybe Double
safeDivide _ 0 = Nothing
safeDivide x y = Just (x / y)

main :: IO ()
main = do
    putStrLn "=== Calcul de la vitesse (km/h) ==="
    putStrLn "Entrez la distance parcourue (en km) :"
    distanceInput <- getLine
    putStrLn "Entrez le temps écoulé (en heures) :"
    timeInput <- getLine

    let maybeDistance = readMaybe distanceInput :: Maybe Double
        maybeTime     = readMaybe timeInput :: Maybe Double

    case (maybeDistance, maybeTime) of
        (Nothing, _) -> putStrLn "Erreur : la distance doit être un nombre valide."
        (_, Nothing) -> putStrLn "Erreur : le temps doit être un nombre valide."
        (Just d, Just t) -> 
            case safeDivide d t of
                Nothing   -> putStrLn "Erreur : le temps ne peut pas être zéro."
                Just v    -> putStrLn ("La vitesse est : " ++ show v ++ " km/h")
```

---

### Explications détaillées

1. **Parsing sécurisé avec `readMaybe`**

   * On convertit les saisies utilisateur en `Maybe Double`.
   * Si la conversion échoue, on obtient `Nothing`, géré par le `case`.

2. **Division protégée avec `safeDivide`**

   * Empêche la division par zéro (retourne `Nothing` si `t = 0`).

3. **Gestion combinée avec double `case`**

   * Premier `case` : vérifie que les deux valeurs ont bien été parsées.
   * Deuxième `case` : vérifie que la division est possible.

4. **Résultat final**

   * Si tout va bien → affiche la vitesse en km/h.
   * Sinon → affiche le message d’erreur correspondant.

---

### 🧩 Exemples d’exécution

 **Entrées valides :**

```
=== Calcul de la vitesse (km/h) ===
Entrez la distance parcourue (en km) :
150
Entrez le temps écoulé (en heures) :
3
La vitesse est : 50.0 km/h
```

 **Entrée non numérique :**

```
Entrez la distance parcourue (en km) :
abc
Entrez le temps écoulé (en heures) :
3
Erreur : la distance doit être un nombre valide.
```

 **Temps nul :**

```
Entrez la distance parcourue (en km) :
120
Entrez le temps écoulé (en heures) :
0
Erreur : le temps ne peut pas être zéro.
```

