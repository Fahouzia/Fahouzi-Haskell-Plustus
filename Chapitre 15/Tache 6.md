**HC15T6 : Parsing d’entrée utilisateur avec `readMaybe`**

---

###  Objectif

Lire une entrée utilisateur, **la convertir en nombre de façon sécurisée**
(sans erreur si la saisie est invalide) en utilisant `readMaybe` du module `Text.Read`.

* Si la saisie n’est **pas un nombre**, afficher un message d’erreur.
* Sinon, afficher le double de ce nombre, par exemple.

---

###  Code 

```haskell
-- HC15T6 : Parsing d’entrée utilisateur avec readMaybe

import Text.Read (readMaybe)

main :: IO ()
main = do
    putStrLn "=== Parsing sécurisé avec readMaybe ==="
    putStrLn "Entrez un nombre :"
    input <- getLine

    -- Utilisation de readMaybe pour parser de manière sûre
    let maybeNumber = readMaybe input :: Maybe Double

    case maybeNumber of
        Nothing   -> putStrLn "Erreur : entrée invalide, veuillez entrer un nombre."
        Just n    -> putStrLn ("Le double de ce nombre est : " ++ show (2 * n))
```

---

### 🔍 Explications détaillées

1. **Importation du module**

   ```haskell
   import Text.Read (readMaybe)
   ```

   Le module `Text.Read` fournit la fonction `readMaybe`, qui essaie de convertir une chaîne (`String`) en une valeur d’un type donné **sans provoquer d’erreur**.

2. **Pourquoi `readMaybe` ?**

   * Avec `read`, une entrée invalide (ex : `"abc"`) provoque une **erreur d’exécution**.
   * Avec `readMaybe`, on obtient simplement `Nothing`, ce qui permet de gérer le cas proprement.

3. **Type `Maybe`**

   * `readMaybe` retourne `Maybe a`, donc :

     * `Just valeur` si la conversion réussit.
     * `Nothing` si la conversion échoue.

4. **Bloc `case`**

   * Si `Nothing`, on affiche un message d’erreur.
   * Si `Just n`, on affiche le résultat du calcul.

---

### 🧩 Exemple d’exécution

✅ **Cas valide :**

```
=== Parsing sécurisé avec readMaybe ===
Entrez un nombre :
12.5
Le double de ce nombre est : 25.0
```

❌ **Cas invalide :**

```
=== Parsing sécurisé avec readMaybe ===
Entrez un nombre :
abc
Erreur : entrée invalide, veuillez entrer un nombre.
```

---

Souhaites-tu que je te montre une **version combinée avec la division sécurisée (HC15T5 + HC15T6)**, où les deux entrées sont parsées avec `readMaybe` *et* la division est sécurisée avec `Maybe` ?
