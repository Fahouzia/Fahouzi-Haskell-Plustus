HC5T8 : Style point-free

En style **point-free**, on supprime l’argument `x` et on utilise directement une fonction partielle :

```haskell
-- Version point-free de addFive
addFive :: Int -> Int
addFive = (+5)  -- pas besoin de mentionner x

-- Fonction main pour tester
main :: IO ()
main = do
    print (addFive 10)  -- Résultat : 15
    print (addFive 0)   -- Résultat : 5
    print (addFive (-3))-- Résultat : 2


```

**Explication :**

* `(+5)` est une fonction qui prend un nombre et lui ajoute 5.
* On n’a plus besoin de mentionner `x`, donc la fonction devient **point-free**.
* Exemple : `addFive 3` renvoie `8`.

C’est exactement la même fonction que `addFive x = x + 5`, mais sans écrire explicitement l’argument.


### 1️La fonction originale

```haskell
addFive x = x + 5
```

* Ici, `addFive` est une fonction qui prend **un argument `x`** et retourne **`x + 5`**.
* Exemple : `addFive 3` → `3 + 5` → `8`.

---

### 2️ Comprendre `(+)` comme fonction

En Haskell, **`+` est un opérateur** qui peut aussi être utilisé comme une fonction si on le met entre parenthèses :

```haskell
(+) 3 5  -- résultat : 8
```

* `(+)` est maintenant traité comme une fonction qui prend deux arguments.

---

### 3️ Fonction partielle

Si on écrit seulement :

```haskell
(+5)
```

* On crée une **fonction qui attend un nombre et lui ajoute 5**.
* Exemple :

```haskell
(+5) 2   -- résultat : 7
(+5) 10  -- résultat : 15
```

C’est exactement ce que fait `addFive`.

---

### 4️ Le style point-free

En Haskell, **le style point-free consiste à ne pas écrire explicitement l’argument**.

Donc au lieu de :

```haskell
addFive x = x + 5
```

On écrit :

```haskell
addFive = (+5)
```

* Ici, `addFive` est **directement défini comme la fonction `(+5)`**.
* Quand tu fais `addFive 4`, Haskell applique la fonction `(+5)` à 4 → `4 + 5 = 9`.

---
