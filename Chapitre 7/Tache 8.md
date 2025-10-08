**HC7T8 – Parser une valeur avec `Read`**.

##  Objectif

Créer une fonction :

```haskell
parseShape :: String -> Shape
```

 Elle prend une chaîne de caractères (String) et retourne un objet de type `Shape`,
en utilisant la **classe de type `Read`**.

---

##  Code 

```haskell
-- HC7T8 : Parser une valeur avec Read

-- Définition du type Shape avec Show et Read
data Shape = Circle Double | Rectangle Double Double
    deriving (Show, Read)

-- Fonction pour parser une chaîne de caractères en Shape
parseShape :: String -> Shape
parseShape s = read s :: Shape

-- Fonction principale main pour tester
main :: IO ()
main = do
    let input1 = "Circle 4.5"
    let input2 = "Rectangle 3.0 6.0"

    let shape1 = parseShape input1
    let shape2 = parseShape input2

    putStrLn ("Chaîne : " ++ input1 ++ " -> " ++ show shape1)
    putStrLn ("Chaîne : " ++ input2 ++ " -> " ++ show shape2)
```

---

##  Explication pas à pas

### 1️⃣ Définir le type `Shape`

```haskell
data Shape = Circle Double | Rectangle Double Double
    deriving (Show, Read)
```

* `Shape` a deux constructeurs :

  * `Circle Double` → représente un cercle (rayon)
  * `Rectangle Double Double` → représente un rectangle (longueur, largeur)

* On **derive** deux classes importantes :

  * `Show` → permet d’afficher une forme sous forme de texte (`show`)
  * `Read` → permet de **convertir du texte en valeur Haskell** (`read`)

---

### 2️⃣ Fonction `parseShape`

```haskell
parseShape :: String -> Shape
parseShape s = read s :: Shape
```

* `read` est une fonction intégrée en Haskell :

  ```haskell
  read :: Read a => String -> a
  ```

  Elle transforme une chaîne de caractères en valeur d’un type donné.

* Ici, on précise le type cible avec `:: Shape`
   pour indiquer à Haskell qu’on veut lire un `Shape`.

---

### 3️⃣ Fonction `main`

```haskell
main :: IO ()
main = do
    let input1 = "Circle 4.5"
    let input2 = "Rectangle 3.0 6.0"

    let shape1 = parseShape input1
    let shape2 = parseShape input2

    putStrLn ("Chaîne : " ++ input1 ++ " -> " ++ show shape1)
    putStrLn ("Chaîne : " ++ input2 ++ " -> " ++ show shape2)
```

* On crée deux chaînes représentant des formes.
* On appelle `parseShape` pour les transformer en vraies valeurs Haskell.
* Puis on affiche le résultat.

---

### 🧾 Exemple de sortie

```
Chaîne : Circle 4.5 -> Circle 4.5
Chaîne : Rectangle 3.0 6.0 -> Rectangle 3.0 6.0
```

---

###  Remarques importantes

1. La chaîne passée à `read` doit correspondre **exactement** à la syntaxe Haskell du type :

   * ✅ `"Circle 3.0"`
   * ✅ `"Rectangle 2.0 4.5"`
   * ❌ `"circle(3.0)"` (ça plantera)

2. Si la chaîne n’est pas conforme, `read` provoque une erreur d’exécution.
    On peut utiliser `reads` à la place pour éviter cela et tester la validité du format.

---
