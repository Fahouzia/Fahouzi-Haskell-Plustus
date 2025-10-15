HC10T9 : Classe de type MinMax

### **Code  :**

```haskell
-- HC10T9 : Classe de type MinMax

-- Définition de la classe MinMax
class MinMax a where
    minValue :: a
    maxValue :: a

-- Instance pour le type Int
instance MinMax Int where
    minValue = minBound :: Int
    maxValue = maxBound :: Int

-- Fonction principale pour tester
main :: IO ()
main = do
    putStrLn ("Valeur minimale (Int) : " ++ show (minValue :: Int))
    putStrLn ("Valeur maximale (Int) : " ++ show (maxValue :: Int))
```

---

###  **Explication pas à pas :**

#### 1. **Définition de la classe `MinMax`**

```haskell
class MinMax a where
    minValue :: a
    maxValue :: a
```

* On crée une **classe de type** `MinMax` pour représenter des types qui ont :

  * une **valeur minimale** (`minValue`)
  * une **valeur maximale** (`maxValue`)
* C’est une abstraction utile pour des types numériques ou bornés.

---

#### 2. **Instance pour `Int`**

```haskell
instance MinMax Int where
    minValue = minBound :: Int
    maxValue = maxBound :: Int
```

* Le type `Int` appartient déjà à la classe standard `Bounded` (qui définit `minBound` et `maxBound`).
* On utilise donc ces valeurs existantes :

  * `minBound :: Int` → plus petit entier représentable.
  * `maxBound :: Int` → plus grand entier représentable.
* En général :

  * sur 64 bits : `minBound = -9223372036854775808`
  * `maxBound = 9223372036854775807`

---

#### 3. **Fonction principale (`main`)**

* On affiche la valeur minimale et maximale pour le type `Int` :

  ```haskell
  putStrLn ("Valeur minimale (Int) : " ++ show (minValue :: Int))
  putStrLn ("Valeur maximale (Int) : " ++ show (maxValue :: Int))
  ```

---

###  **Sortie attendue dans le terminal :**

```
Valeur minimale (Int) : -9223372036854775808
Valeur maximale (Int) : 9223372036854775807
```

---

###  **Remarque :**

Tu pourrais facilement **étendre** cette classe pour d’autres types,
par exemple `Char` ou `Bool` :

```haskell
instance MinMax Char where
    minValue = minBound
    maxValue = maxBound

instance MinMax Bool where
    minValue = False
    maxValue = True
```
