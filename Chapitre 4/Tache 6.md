HC4T6 - Tâche 6 : Identifier le contenu d'une liste par pattern matching

code 

```haskell
-- Définition de la fonction whatsInsideThisList
whatsInsideThisList :: [a] -> String
whatsInsideThisList []       = "La liste est vide."
whatsInsideThisList [x]      = "La liste contient un élément."
whatsInsideThisList [x,y]    = "La liste contient deux éléments."
whatsInsideThisList (x:y:_)  = "La liste contient plus de deux éléments."

-- Exemples de test
main :: IO ()
main = do
    print (whatsInsideThisList [])           -- "La liste est vide."
    print (whatsInsideThisList [10])        -- "La liste contient un élément."
    print (whatsInsideThisList [10, 20])    -- "La liste contient deux éléments."
    print (whatsInsideThisList [1,2,3,4])   -- "La liste contient plus de deux éléments."
```

Explication ligne par ligne

```haskell
whatsInsideThisList :: [a] -> String
```

* La fonction prend une **liste de n’importe quel type** `[a]` et retourne une **chaîne** `String`.
* Le type `[a]` est polymorphe, donc la fonction fonctionne pour `Int`, `Char`, etc.

```haskell
whatsInsideThisList [] = "La liste est vide."
```

* Cas où la liste est **vide**.

```haskell
whatsInsideThisList [x] = "La liste contient un élément."
```

* Cas où la liste contient **exactement un élément**.
* `[x]` signifie « une liste avec un seul élément que l’on appelle `x` ».

```haskell
whatsInsideThisList [x,y] = "La liste contient deux éléments."
```

* Cas où la liste contient **exactement deux éléments**.

```haskell
whatsInsideThisList (x:y:_) = "La liste contient plus de deux éléments."
```

* Cas pour **toutes les listes de plus de deux éléments**.
* `(x:y:_)` signifie « liste dont les deux premiers éléments sont `x` et `y`, et `_` représente le reste que l’on ignore ».

```haskell
main :: IO ()
main = do
    print (whatsInsideThisList [])
    print (whatsInsideThisList [10])
    print (whatsInsideThisList [10, 20])
    print (whatsInsideThisList [1,2,3,4])
```

* `main` teste la fonction pour différentes tailles de liste.
* `print` affiche le message correspondant.

```haskell
whatsInsideThisList :: [a] -> String
```

* **Type de la fonction** :

  * `[a]` → une **liste d’éléments de n’importe quel type** (`Int`, `Char`, etc.).
  * `String` → la fonction renvoie une chaîne de caractères.
* La fonction est **polymorphe**, elle fonctionne avec n’importe quel type d’éléments.

---

```haskell
whatsInsideThisList [] = "La liste est vide."
```

* Cas où la liste est **vide**.
* `[]` est la **liste vide**.
* La fonction renvoie le message `"La liste est vide."`.

---

```haskell
whatsInsideThisList [x] = "La liste contient un élément."
```

* Cas où la liste contient **exactement un élément**.
* `[x]` signifie « une liste avec **un seul élément**, que l’on appelle `x` ».
* La valeur de `x` n’est pas utilisée ici, on s’intéresse seulement au **nombre d’éléments**.

---

```haskell
whatsInsideThisList [x,y] = "La liste contient deux éléments."
```

* Cas où la liste contient **exactement deux éléments**.
* `[x,y]` correspond à une liste avec deux éléments : `x` et `y`.
* Comme pour le cas précédent, les valeurs elles-mêmes ne sont pas utilisées.

---

```haskell
whatsInsideThisList (x:y:_) = "La liste contient plus de deux éléments."
```

* Cas pour toutes les listes **de plus de deux éléments**.
* `(x:y:_)` se lit :

  * `x` → premier élément
  * `y` → deuxième élément
  * `_` → reste de la liste, que l’on **ignore** (wildcard).
* Cela capture toutes les listes qui ont **au moins trois éléments**.

---

```haskell
main :: IO ()
main = do
    print (whatsInsideThisList [])
    print (whatsInsideThisList [10])
    print (whatsInsideThisList [10, 20])
    print (whatsInsideThisList [1,2,3,4])
```

* `main :: IO ()` → point d’entrée du programme.
* `do` permet de **séquencer plusieurs actions IO** (ici, plusieurs affichages).
* `print (...)` → affiche le message renvoyé par la fonction pour différentes listes.
* Chaque appel teste un cas spécifique : vide, un élément, deux éléments, plus de deux éléments.

---


1. `[]` → liste vide
2. `[x]` → un élément
3. `[x,y]` → deux éléments
4. `(x:y:_)` → plus de deux éléments





