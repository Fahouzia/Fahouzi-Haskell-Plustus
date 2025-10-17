**HC14T3 : Extension NumericUnderscores**

---

###  **Code

```haskell
{-# LANGUAGE NumericUnderscores #-}

module Main where

main :: IO ()
main = do
    -- Déclaration de grands nombres avec underscores pour améliorer la lisibilité
    let populationMonde = 8_100_000_000        -- 8,1 milliards
    let distanceTerreSoleil = 149_600_000_000  -- en mètres
    let prixVoiture = 25_999_999               -- en unités monétaires

    putStrLn "=== Exemple d'utilisation de NumericUnderscores ==="
    putStrLn ("Population mondiale : " ++ show populationMonde)
    putStrLn ("Distance Terre-Soleil (m) : " ++ show distanceTerreSoleil)
    putStrLn ("Prix d'une voiture de luxe : " ++ show prixVoiture)
```

---

###  **Explications pas-à-pas**

1. **Extension activée :**

   ```haskell
   {-# LANGUAGE NumericUnderscores #-}
   ```

   → Cette extension permet d’utiliser des underscores `_` dans les littéraux numériques pour **améliorer la lisibilité** des grands nombres, sans changer leur valeur.

2. **Variables avec grands nombres :**

   ```haskell
   let populationMonde = 8_100_000_000
   ```

   → Cela équivaut à `8100000000`, mais bien plus lisible.

3. **Affichage :**
   On utilise `show` pour convertir les valeurs numériques en chaînes de caractères et `putStrLn` pour les afficher.

---

###  **Exécution dans le terminal**

Pour lancer le programme :

```bash
runhaskell HC14T3.hs
```

ou, si vous utilisez un projet Cabal :

```bash
cabal run
```

