HC15T1 : Gérer les exceptions lors de la lecture d’un fichier et du calcul de la vitesse

```haskell
--- HC15T1.hs
import System.IO
import Control.Exception
import Text.Read (readMaybe)

-- Lecture sécurisée d'un fichier
readFileSafe :: FilePath -> IO (Either String String)
readFileSafe path = try (readFile path) >>= \case
    Left e  -> return $ Left ("Erreur lors de la lecture du fichier : " ++ show (e :: IOException))
    Right content -> return $ Right content

-- Calcul sécurisé de la vitesse
calculateSpeed :: IO ()
calculateSpeed = do
    putStrLn "Entrez la distance parcourue en mètres :"
    distInput <- getLine
    putStrLn "Entrez le temps écoulé en secondes :"
    timeInput <- getLine
    case (readMaybe distInput :: Maybe Double, readMaybe timeInput :: Maybe Double) of
        (Just distance, Just time) ->
            if time == 0
                then putStrLn "Erreur : le temps ne peut pas être zéro."
                else putStrLn $ "La vitesse est " ++ show (distance / time) ++ " m/s."
        _ -> putStrLn "Erreur : veuillez entrer des nombres valides."

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez le chemin du fichier à lire :"
    filePath <- getLine
    fileContent <- readFileSafe filePath
    case fileContent of
        Left err -> putStrLn err
        Right content -> do
            putStrLn "Contenu du fichier :"
            putStrLn content
            calculateSpeed

```

---

### 🔹 Explications pas-à-pas :

1. **Import des modules nécessaires :**

   * `System.IO` pour la lecture/écriture de fichiers.
   * `Control.Exception` pour gérer les exceptions.
   * `Text.Read (readMaybe)` pour convertir en nombre en toute sécurité sans planter le programme.

2. **Lecture sécurisée d’un fichier (`readFileSafe`) :**

   * La fonction `try` renvoie `Either IOException String`.

     * `Left e` → une exception s’est produite.
     * `Right content` → le fichier a été lu correctement.
   * On retourne un `Either String String` pour indiquer l’erreur ou le contenu.

3. **Saisie utilisateur et calcul de la vitesse (`calculateSpeed`) :**

   * `readMaybe` permet de convertir une chaîne en `Double` sans lancer d’exception si la saisie est invalide.
   * On vérifie que le temps n’est pas zéro pour éviter une division par zéro.
   * En cas d’entrée invalide, on affiche un message d’erreur clair.

4. **Fonction `main` :**

   * Demande le chemin du fichier.
   * Lit le fichier avec `readFileSafe` et gère les erreurs.
   * Affiche le contenu si la lecture a réussi.
   * Appelle `calculateSpeed` pour interagir avec l’utilisateur.

---

