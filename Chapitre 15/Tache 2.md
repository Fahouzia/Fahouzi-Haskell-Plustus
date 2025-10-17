

## **HC15T2.hs : Voiture autonome basique**

```haskell
-- HC15T2.hs
import Text.Read (readMaybe)

-- Définition des feux
data Feu = Rouge | Orange | Vert deriving (Show, Read, Eq)

-- Réaction de la voiture selon le feu
reactionVoiture :: Feu -> String
reactionVoiture Rouge  = "Arrêt complet."
reactionVoiture Orange = "Ralentir."
reactionVoiture Vert   = "Avancer."

-- Lecture sécurisée d'un feu depuis l'utilisateur
readFeu :: IO Feu
readFeu = do
    putStrLn "Entrez la couleur du feu (Rouge, Orange, Vert) :"
    input <- getLine
    case reads input :: [(Feu, String)] of
        [(feu, "")] -> return feu
        _ -> do
            putStrLn "Entrée invalide ! Veuillez entrer Rouge, Orange ou Vert."
            readFeu  -- redemande jusqu'à ce que ce soit correct

-- Fonction principale
main :: IO ()
main = do
    feu <- readFeu
    putStrLn $ "Réaction de la voiture : " ++ reactionVoiture feu
```

---

###  Explications :

1. **Type `Feu`**

   * `data Feu = Rouge | Orange | Vert` → représente les trois couleurs de feu.
   * `deriving (Show, Read, Eq)` → permet d’afficher, lire et comparer les feux facilement.

2. **Fonction `reactionVoiture`**

   * Retourne la réaction adaptée selon la couleur du feu.

3. **Fonction `readFeu`**

   * Lit la saisie utilisateur et tente de convertir en `Feu` avec `reads`.
   * Si l’entrée est invalide → redemande jusqu’à ce que ce soit correct.

4. **Fonction `main`**

   * Lit le feu, puis affiche la réaction de la voiture.
   * Programme robuste → aucune entrée invalide ne fait planter le programme.

---
