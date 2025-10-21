

 **HC15T10 : Programme de vitesse utilisant Either et les exceptions IO**
 
---

##  Objectif

Créer un programme qui :

1. Lit la **distance** et le **temps** depuis un **fichier texte** ;
2. Utilise `try` pour **capturer les erreurs IO** (fichier introuvable, permissions, etc.) ;
3. Utilise `Either` pour **gérer les erreurs de calcul** (par exemple, division par zéro ou données invalides) ;
4. Calcule la **vitesse = distance / temps** si tout est valide.

---

## Code 

```haskell
-- HC15T10 : Programme de vitesse utilisant Either et les exceptions IO

import System.IO
import Control.Exception (try, IOException)
import Text.Read (readMaybe)

-- Fonction de division sécurisée avec Either
safeDivide :: Double -> Double -> Either String Double
safeDivide _ 0 = Left "Erreur : le temps ne peut pas être zéro."
safeDivide d t = Right (d / t)

-- Fonction de parsing sûre avec Either
parseValue :: String -> Either String Double
parseValue s =
    case readMaybe s :: Maybe Double of
        Nothing -> Left ("Erreur : valeur invalide -> " ++ s)
        Just n  -> Right n

main :: IO ()
main = do
    putStrLn "=== Calcul de vitesse (km/h) avec gestion hybride d’erreurs ==="
    putStrLn "Entrez le nom du fichier contenant distance et temps :"
    fileName <- getLine

    -- Tentative de lecture du fichier avec gestion d’exception IO
    fileResult <- try (readFile fileName) :: IO (Either IOException String)

    case fileResult of
        Left ioErr -> putStrLn ("Erreur d'accès au fichier : " ++ show ioErr)
        Right content -> do
            let linesData = lines content
            case linesData of
                (dStr:tStr:_) -> do
                    let eDistance = parseValue dStr
                        eTime     = parseValue tStr

                    case (eDistance, eTime) of
                        (Left err, _) -> putStrLn err
                        (_, Left err) -> putStrLn err
                        (Right d, Right t) ->
                            case safeDivide d t of
                                Left err   -> putStrLn err
                                Right v    -> putStrLn ("Vitesse = " ++ show v ++ " km/h")
                _ -> putStrLn "Erreur : le fichier doit contenir au moins deux lignes (distance et temps)."
```

---

##  Exemple de fichier d’entrée

 **fichier : `vitesse.txt`**

```
150
3
```

---

## 💡 Exemple d’exécution

 **Cas normal :**

```
=== Calcul de vitesse (km/h) avec gestion hybride d’erreurs ===
Entrez le nom du fichier contenant distance et temps :
vitesse.txt
Vitesse = 50.0 km/h
```

❌ **Cas fichier inexistant :**

```
Entrez le nom du fichier contenant distance et temps :
inexistant.txt
Erreur d'accès au fichier : inexistant.txt: openFile: does not exist (No such file or directory)
```

❌ **Cas temps nul :**

```
150
0
```

→ Résultat :

```
Erreur : le temps ne peut pas être zéro.
```

 **Cas données invalides :**

```
abc
5
```

→ Résultat :

```
Erreur : valeur invalide -> abc
```

---

##  Explications détaillées

### 1. **Gestion IO avec `try`**

* On utilise :

  ```haskell
  fileResult <- try (readFile fileName) :: IO (Either IOException String)
  ```

  pour capturer toute erreur liée à la lecture du fichier.
* Si erreur : `Left ioErr`
* Si succès : `Right content`

### 2. **Gestion pure avec `Either`**

* `parseValue` convertit le texte en nombre (retourne `Left` en cas d’échec).
* `safeDivide` vérifie la division par zéro (retourne `Left` si temps = 0).

### 3. **Combinaison des deux mondes**

* Les erreurs de **fichier** sont gérées dans le *monde IO*.
* Les erreurs de **calcul/parsing** sont gérées de manière *pure* via `Either`.

---

##  En résumé

| Type d’erreur             | Gestion      | Type utilisé         | Exemple                   |
| ------------------------- | ------------ | -------------------- | ------------------------- |
| Erreur d’accès au fichier | Exception IO | `try`, `IOException` | Fichier inexistant        |
| Erreur de parsing         | Pure         | `Either String`      | `"abc"` → non convertible |
| Division par zéro         | Pure         | `Either String`      | `t = 0`                   |

---
