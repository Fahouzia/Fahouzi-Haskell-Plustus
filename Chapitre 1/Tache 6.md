HC1T6 - Tâche 6 : Utilisation de signatures de type

CODE 

```haskell
-- Définition de la fonction addNumbers avec sa signature de type
addNumbers :: Int -> Int -> Int
addNumbers x y = x + y

-- Exemple d'utilisation dans main
main :: IO ()
main = do
    print (addNumbers 5 7)  -- Affiche 12
```

---

EXPLICATION 

### Signature de type

```haskell
addNumbers :: Int -> Int -> Int
```

* `addNumbers` est le nom de la fonction.
* `::` signifie "a pour type".
* `Int -> Int -> Int` veut dire que la fonction prend **deux arguments de type `Int`** (entiers) et retourne un **résultat de type `Int`**.
* En Haskell, `->` est associatif à droite, donc
  `Int -> Int -> Int` est équivalent à
  `Int -> (Int -> Int)` : la fonction prend un `Int` et retourne une fonction qui prend un autre `Int` et retourne un `Int`.

### Définition de la fonction

```haskell
addNumbers x y = x + y
```

* `x` et `y` sont les deux paramètres entiers.
* Le corps de la fonction est simplement la somme de `x` et `y` avec l’opérateur `+`.
* L’opérateur `+` est défini pour les types numériques comme `Int`.

### Fonction principale `main`

```haskell
main = do
    print (addNumbers 5 7)
```

* `main` est la fonction d'entrée du programme, de type `IO ()`.
* Elle utilise la fonction `print` pour afficher le résultat de `addNumbers X Y`, soit `x+y`.


