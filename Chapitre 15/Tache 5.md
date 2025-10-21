 **HC15T5 : Fonction de division sécurisée avec `Maybe`**

---

###  Objectif

Créer une fonction de division sécurisée qui :

* prend deux nombres en entrée (numérateur et dénominateur),
* retourne `Nothing` si le dénominateur est zéro (pour éviter une erreur),
* retourne `Just résultat` sinon.

---

###  Code 

```haskell
-- HC15T5 : Fonction de division sécurisée avec Maybe

-- Définition de la fonction
safeDivide :: Double -> Double -> Maybe Double
safeDivide _ 0 = Nothing           -- Cas où le dénominateur est 0
safeDivide x y = Just (x / y)      -- Cas normal

-- Fonction principale pour démontrer l'utilisation
main :: IO ()
main = do
    putStrLn "=== Division sécurisée ==="
    putStrLn "Entrez le numérateur :"
    numInput <- getLine
    putStrLn "Entrez le dénominateur :"
    denInput <- getLine

    let numerator   = read numInput :: Double
        denominator = read denInput :: Double
        result      = safeDivide numerator denominator

    case result of
        Nothing   -> putStrLn "Erreur : division par zéro interdite !"
        Just val  -> putStrLn ("Résultat : " ++ show val)
```

---

###  Explications détaillées

1. **Type `Maybe`** :

   * `Maybe a` est un type générique qui peut contenir soit :

     * `Just a` (valeur valide)
     * `Nothing` (absence de valeur, erreur, ou cas exceptionnel)
   * Cela permet d’éviter les erreurs d’exécution comme la division par zéro.

2. **Pattern matching dans `safeDivide`** :

   * Si le dénominateur est `0`, on retourne `Nothing`.
   * Sinon, on effectue la division et on retourne `Just (x / y)`.

3. **Bloc `main`** :

   * On lit les deux nombres entrés par l’utilisateur.
   * On appelle `safeDivide`.
   * On utilise une expression `case` pour distinguer le cas `Nothing` (erreur) du cas `Just`.

---

###  Exemple d’exécution

```
=== Division sécurisée ===
Entrez le numérateur :
10
Entrez le dénominateur :
2
Résultat : 5.0
```

```
=== Division sécurisée ===
Entrez le numérateur :
10
Entrez le dénominateur :
0
Erreur : division par zéro interdite !
```

