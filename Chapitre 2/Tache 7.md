HC2T7 – Expressions booléennes

## 1. Expression qui retourne `True` avec `&&`

```haskell
True && True   -- Résultat : True
```

**Explication :**
L’opérateur `&&` est **ET logique** : il retourne `True` seulement si **les deux côtés** sont `True`.

---

## 2. Expression qui retourne `False` avec `||`

```haskell
False || False   -- Résultat : False
```

**Explication :**
L’opérateur `||` est **OU logique** : il retourne `True` si **au moins un** des deux côtés est `True`. Ici, les deux sont `False`, donc le résultat est `False`.

---

##  3. Expression qui retourne `True` avec `not`

```haskell
not False   -- Résultat : True
```

**Explication :**
`not` **inverse** la valeur logique. Donc `not False` devient `True`.

---

##  4. Une comparaison qui retourne `False`

```haskell
5 > 10   -- Résultat : False
```

**Explication :**
On compare `5` à `10`. Comme `5` n’est pas supérieur à `10`, le résultat est `False`.

---

les expression le test se fait AVEC GHCI
```haskell
-- 1. True avec &&
expr1 = True && True

-- 2. False avec ||
expr2 = False || False

-- 3. True avec not
expr3 = not False

-- 4. Comparaison donnant False
expr4 = 5 > 10
```

POUR LE TEST ON PEUT TAPER DIRECTEMENT 

```haskell
:t True && True
:t False || False
:t not False
:t 5 > 10
```
