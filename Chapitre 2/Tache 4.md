HC2T4 - Tâche 4 : Notation préfixe et infixe


CODE 

```haskell
main :: IO ()
main = do
    -- Notation préfixe
    print ((+) 5 3)         -- Affiche 8
    print ((*) 10 4)        -- Affiche 40
    print ((&&) True False) -- Affiche False

    -- Notation infixe
    print (7 + 2)           -- Affiche 9
    print (6 * 5)           -- Affiche 30
    print (True && False)   -- Affiche False
```

---

EXPLICATION

## 1. Notation préfixe

**En Haskell, la notation préfixe** consiste à écrire la fonction **avant ses arguments**, comme :

```haskell
f x y
```

Pour les opérateurs, tu mets l’opérateur entre parenthèses pour l’utiliser comme une fonction.

---

### Expressions données à écrire en notation préfixe

| Expression infixe | Notation préfixe correcte |
| ----------------- | ------------------------- |
| `5 + 3`           | `(+) 5 3`                 |
| `10 * 4`          | `(*) 10 4`                |
| `True && False`   | `(&&) True False`         |

---

## 2. Notation infixe

**La notation infixe** est la forme classique où l’opérateur est écrit **entre** les deux arguments, par exemple :

```haskell
x + y
```

On peut transformer des appels de fonction en notation infixe uniquement si la fonction est un opérateur (une fonction symbolique ou un opérateur entre backticks).

---

### Fonctions données à écrire en notation infixe

| Expression préfixe | Notation infixe correcte |
| ------------------ | ------------------------ |
| `(+) 7 2`          | `7 + 2`                  |
| `(*) 6 5`          | `6 * 5`                  |
| `(&&) True False`  | `True && False`          |

---

* En Haskell, les opérateurs comme `+`, `*`, `&&` sont **des fonctions infixes par défaut**.
* Pour les utiliser comme fonctions en **notation préfixe**, il faut les entourer de parenthèses, par exemple `(+)`, `(*)`.
* Ainsi, `(+) 5 3` signifie : appliquer la fonction `+` à `5` et `3`.

### Notation infixe

* C’est la façon normale d’écrire les opérations :
  `5 + 3`, `True && False`, etc.
* Ici, les opérateurs apparaissent **entre** leurs deux arguments.


