HC15T3 : Définir et lancer une exception personnalisée pour les feux
---

code 

```haskell
-- HC15T3.hs
import Control.Exception
import System.IO

-- Définition d'une exception personnalisée
data FeuException = FeuInvalide String deriving (Show)
instance Exception FeuException

-- Vérification d'un feu : lance une exception si invalide
verifierFeu :: String -> IO ()
verifierFeu couleur =
    if couleur `elem` ["Rouge", "Orange", "Vert"]
        then putStrLn "Feu valide."
        else throwIO (FeuInvalide couleur)  -- lance l'exception

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez la couleur du feu :"
    couleur <- getLine
    verifierFeu couleur
```

---

### Explications

1. **Création de l’exception personnalisée**

   * `data FeuException = FeuInvalide String deriving (Show)`
   * On dérive `Show` pour pouvoir afficher l’exception.
   * `instance Exception FeuException` → rend le type utilisable avec `throwIO` et `catch`.

2. **Fonction `verifierFeu`**

   * Vérifie si la couleur est dans la liste des feux valides (`Rouge`, `Orange`, `Vert`).
   * Si non → lance l’exception avec `throwIO`.

3. **Fonction `main`**

   * Lit la saisie de l’utilisateur et appelle `verifierFeu`.
   * Si l’utilisateur entre un feu invalide, l’exception est levée.

---

###  Remarque

* Ce code **ne gère pas encore l’exception**. Il montre **comment la lancer**.
* Pour gérer l’exception et afficher un message plutôt que de planter le programme, il faudra utiliser `catch` ou `handle` (c’est HC15T4).

---
