Parfait ! Voici **HC15T4**, la version fonctionnelle qui **intercepte l’exception personnalisée des feux** et affiche un message clair à l’utilisateur sans planter le programme.

---

## **HC15T4.hs : Gestion d’exception pour les feux**

```haskell
-- HC15T4.hs
import Control.Exception
import System.IO

-- Définition de l'exception personnalisée
data FeuException = FeuInvalide String deriving (Show)
instance Exception FeuException

-- Vérification d'un feu : lance une exception si invalide
verifierFeu :: String -> IO ()
verifierFeu couleur =
    if couleur `elem` ["Rouge", "Orange", "Vert"]
        then putStrLn "Feu valide."
        else throwIO (FeuInvalide couleur)  -- lance l'exception

-- Gestionnaire d'exception
gestionFeu :: FeuException -> IO ()
gestionFeu (FeuInvalide couleur) =
    putStrLn $ "Erreur : feu invalide -> " ++ couleur

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez la couleur du feu :"
    couleur <- getLine
    catch (verifierFeu couleur) gestionFeu
```

---

### ✅ Explications

1. **Exception personnalisée**

   * `FeuException` avec le constructeur `FeuInvalide String` pour indiquer quelle couleur est incorrecte.

2. **`verifierFeu`**

   * Vérifie si la couleur saisie est valide.
   * Sinon, lance l’exception avec `throwIO`.

3. **`gestionFeu`**

   * Fonction qui prend l’exception en paramètre et affiche un message clair.
   * Permet au programme de **continuer à tourner** sans planter.

4. **`catch`**

   * Intercepte l’exception levée par `verifierFeu`.
   * Redirige le contrôle vers `gestionFeu`.

---

✅ Résultat :

* Si l’utilisateur saisit `"Rouge"`, `"Orange"` ou `"Vert"` → message **Feu valide**.
* Si saisie invalide → message **Erreur : feu invalide -> …** et le programme ne plante pas.

---

Si tu veux, je peux maintenant te fournir **HC15T5 : Fonction de division sécurisée avec Maybe**, également **robuste et prête à l’exécution**.

Veux‑tu que je fasse ça ?
