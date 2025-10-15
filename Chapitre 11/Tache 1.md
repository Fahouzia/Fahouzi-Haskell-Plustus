**HC11T1 : Instance WeAccept pour Box**

###  Objectif de l’exercice

1. Créer une **classe de type** `WeAccept` qui détermine si un élément est "acceptable".
2. Définir une **instance** de cette classe pour le type **paramétrique `Box a`** (déjà vu précédemment).
3. Écrire une fonction qui **filtre** une liste de `Box` pour ne garder que celles qui sont **acceptées**.

---

### Code 
```haskell
-- Définition du type paramétrique Box
data Box a = Empty | Has a deriving (Show)

-- Définition de la classe de type WeAccept
class WeAccept a where
    weAccept :: a -> Bool

-- Instance de WeAccept pour Box Int
instance WeAccept (Box Int) where
    weAccept Empty = False                      -- Une boîte vide n'est pas acceptée
    weAccept (Has x) = x > 0                    -- On accepte seulement les valeurs positives

-- Fonction pour retourner la liste des boîtes acceptées
acceptedBoxes :: [Box Int] -> [Box Int]
acceptedBoxes boxes = filter weAccept boxes

-- Fonction principale pour tester
main :: IO ()
main = do
    let boxes = [Empty, Has 10, Has (-5), Has 0, Has 7]
    putStrLn "Liste de boîtes initiale :"
    print boxes
    putStrLn "\nBoîtes acceptées :"
    print (acceptedBoxes boxes)
```

---

###Explication pas à pas

#### 1️ Type `Box a`

```haskell
data Box a = Empty | Has a deriving (Show)
```

* `Box` est un type **paramétrique** : il peut contenir une valeur de **n’importe quel type** `a`.
* `Empty` → boîte vide.
* `Has a` → boîte contenant une valeur.
* `deriving (Show)` permet d’afficher les boîtes.

---

#### 2️Classe de type `WeAccept`

```haskell
class WeAccept a where
    weAccept :: a -> Bool
```

* Une **classe de type** définit un **comportement général**.
* Ici, tout type qui fait partie de `WeAccept` doit définir **comment savoir s’il est acceptable** (`weAccept`).

---

#### 3️ Instance pour `Box Int`

```haskell
instance WeAccept (Box Int) where
    weAccept Empty = False
    weAccept (Has x) = x > 0
```

* On limite ici l’instance aux **boîtes contenant des entiers (`Int`)**.
* Une boîte **vide** n’est **jamais acceptée**.
* Une boîte contenant un entier positif (`> 0`) est **acceptée**.
* Si la boîte contient un nombre négatif ou zéro, elle **n’est pas acceptée**.

---

#### 4️ Fonction `acceptedBoxes`

```haskell
acceptedBoxes :: [Box Int] -> [Box Int]
acceptedBoxes boxes = filter weAccept boxes
```

* `filter` applique `weAccept` à chaque élément de la liste.
* Seules les boîtes **acceptées** sont gardées dans la liste finale.

---

#### 5️ Programme principal

```haskell
main :: IO ()
main = do
    let boxes = [Empty, Has 10, Has (-5), Has 0, Has 7]
    putStrLn "Liste de boîtes initiale :"
    print boxes
    putStrLn "\nBoîtes acceptées :"
    print (acceptedBoxes boxes)
```

---

### Résultat attendu

```
Liste de boîtes initiale :
[Empty,Has 10,Has (-5),Has 0,Has 7]

Boîtes acceptées :
[Has 10,Has 7]
```

---

###  Résumé

| Élément                       | Rôle                                       |
| ----------------------------- | ------------------------------------------ |
| `class WeAccept`              | Définit une propriété “acceptable”         |
| `instance WeAccept (Box Int)` | Implémente la logique pour `Box` d’entiers |
| `acceptedBoxes`               | Filtre les boîtes acceptées                |
| `main`                        | Teste le comportement complet              |

---
