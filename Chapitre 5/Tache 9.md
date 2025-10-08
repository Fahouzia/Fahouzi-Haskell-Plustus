HC5T9 : Fonction d’ordre supérieur pour transformer une liste

---

## 1️Comprendre le problème

On veut créer une fonction `transformList` qui :

* Prend **une fonction `f`** comme argument.
* Prend **une liste `xs`**.
* Applique **deux fois** la fonction `f` à chaque élément de la liste.

Exemple :

```haskell
transformList (*2) [1,2,3]
-- Résultat : [4,8,12]  
-- (1*2*2, 2*2*2, 3*2*2)
```

---

## 2️ Définir le type

```haskell
transformList :: (a -> a) -> [a] -> [a]
```

* `(a -> a)` : `f` prend un élément de type `a` et renvoie un élément de type `a`.
* `[a] -> [a]` : la fonction prend une liste d’éléments de type `a` et renvoie une liste transformée.

---

## 3️ Appliquer une fonction à chaque élément d’une liste

En Haskell, la fonction `map` sert exactement à ça :

```haskell
map f [1,2,3]  -- applique f à chaque élément
```

Exemple :

```haskell
map (*2) [1,2,3]  -- résultat : [2,4,6]
```

---

## 4️ Appliquer **deux fois** la fonction `f`

Pour appliquer `f` deux fois à un élément `x` :

```haskell
f (f x)
```

* Par exemple, si `f = (*2)` et `x = 3` :

```haskell
(*2)((*2) 3) = 12
```

* En Haskell, on peut utiliser la **composition de fonctions** :

```haskell
(f . f) x   -- équivalent à f(f(x))
```

---

## 5️ Combiner `map` et l’application double

On veut appliquer `(f . f)` à **tous les éléments** de la liste :

```haskell
map (f . f) xs
```

* `xs` : la liste d’entrée.
* `(f . f)` : applique `f` deux fois à chaque élément.

---

## 6️ Définir la fonction complète

```haskell
transformList :: (a -> a) -> [a] -> [a]
transformList f xs = map (f . f) xs
```

* `transformList` prend une fonction `f` et une liste `xs`.
* Renvoie une nouvelle liste où **chaque élément est transformé deux fois**.

---

## 7️ Exemples d’utilisation

```haskell
-- Doubler deux fois chaque élément
transformList (*2) [1,2,3]
-- [4,8,12]

-- Ajouter 1 deux fois à chaque élément
transformList (+1) [1,2,3]
-- [3,4,5]
```

---


FONCTION 
```haskell
-- Type de la fonction
transformList :: (a -> a) -> [a] -> [a]

-- Définition
transformList f xs = map (f . f) xs
```



1. `transformList` prend **une fonction `f`** et **une liste `xs`**.
2. `f . f` signifie **appliquer `f` deux fois** : `(f . f) x = f (f x)`
3. `map (f . f) xs` applique `(f . f)` à **chaque élément de la liste**.

---

### Exemple d’utilisation :

```haskell
-- Doubler deux fois chaque élément
transformList (*2) [1,2,3,4]
-- Résultat : [4,8,12,16]

-- Ajouter 1 deux fois à chaque élément
transformList (+1) [1,2,3]
-- Résultat : [3,4,5]
```
