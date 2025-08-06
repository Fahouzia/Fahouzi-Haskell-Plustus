HC2T3 - Tâche 3 : Variables immuables


CODE
```haskell
-- Définition des variables immuables

myAge :: Int
myAge = 25

piValue :: Double
piValue = 3.14159

greeting :: String
greeting = "Bonjour Haskell !"

isHaskellFun :: Bool
isHaskellFun = True

-- main pour afficher les valeurs
main :: IO ()
main = do
    putStrLn ("Age : " ++ show myAge)
    putStrLn ("Pi : " ++ show piValue)
    putStrLn greeting
    putStrLn ("Is Haskell fun? " ++ show isHaskellFun)

-- Tentative de modification (ce code provoquera une erreur)
-- myAge = 30  -- Impossible : variable déjà définie, Haskell est immuable
```

---

 Explications

Si tu écris dans ton fichier :

```haskell
myAge = 25
myAge = 30  -- tentative de redéfinition
```

Tu auras une erreur du type :

```
Multiple declarations of ‘myAge’
```

Haskell ne permet pas la redéfinition d’une variable.
Bien sûr ! Voici une explication détaillée de la ligne :

```haskell
putStrLn ("Est-ce que Haskell est amusant ? " ++ show isHaskellFun)
```

---

### 1. `putStrLn`

* C’est une fonction prédéfinie en Haskell.
* Elle sert à **afficher une chaîne de caractères** (`String`) dans la console, suivie d’un retour à la ligne.

---

### 2. `"Est-ce que Haskell est amusant ? "`

* C’est une **chaîne de caractères** littérale, en français.
* Le texte qui sera affiché tel quel.

---

### 3. `++`

* C’est l’opérateur de **concaténation** de chaînes en Haskell.
* Il prend deux chaînes (`String`) et les colle l’une à la suite de l’autre.
* Ici, il colle la phrase + la conversion de la variable `isHaskellFun`.

---

### 4. `show isHaskellFun`

* `isHaskellFun` est une variable de type `Bool` (vaut `True` ou `False`).
* **`show` convertit une valeur en chaîne de caractères** (`String`).
* Donc `show isHaskellFun` transforme `True` en `"True"` ou `False` en `"False"`.
* Cela permet de concaténer un booléen dans une chaîne.

---

## Ensemble

* On crée une chaîne :
  `"Est-ce que Haskell est amusant ? "` + `"True"` (ou `"False"`)
* Puis on l’affiche avec `putStrLn`.

---



On peut faire ça avec une fonction conditionnelle :

```haskell
boolToFrench :: Bool -> String
boolToFrench True = "Oui"
boolToFrench False = "Non"

main = do
    putStrLn ("Est-ce que Haskell est amusant ? " ++ boolToFrench isHaskellFun)
```




