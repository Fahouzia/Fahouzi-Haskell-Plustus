HC10T7 : Classe de type Convertible

###  **Code:**

```haskell

-- Définition de la classe Convertible
class Convertible a b where
    convert :: a -> b

-- Définition du type PaymentMethod
data PaymentMethod = Cash | Card | Cryptocurrency
    deriving (Show)

-- Implémentation de Convertible pour convertir PaymentMethod en String
instance Convertible PaymentMethod String where
    convert Cash           = "Paiement en espèces"
    convert Card           = "Paiement par carte bancaire"
    convert Cryptocurrency = "Paiement en cryptomonnaie"

-- Fonction principale pour tester
main :: IO ()
main = do
    putStrLn ("Cash → " ++ convert Cash)
    putStrLn ("Card → " ++ convert Card)
    putStrLn ("Cryptocurrency → " ++ convert Cryptocurrency)
```

---

###  **Explication pas à pas :**

#### 1. **Création de la classe `Convertible`**

```haskell
class Convertible a b where
    convert :: a -> b
```

* On définit une **classe de type à deux paramètres** `a` et `b`.
* Elle déclare une fonction `convert` qui transforme une valeur de type `a` en une valeur de type `b`.
* C’est une généralisation de l’idée de "conversion" entre types.

---

#### 2. **Définition du type `PaymentMethod`**

```haskell
data PaymentMethod = Cash | Card | Cryptocurrency
    deriving (Show)
```

* Ce type énumère trois **moyens de paiement** :

  * `Cash` → espèces
  * `Card` → carte
  * `Cryptocurrency` → cryptomonnaie

---

#### 3. **Implémentation de la classe `Convertible`**

```haskell
instance Convertible PaymentMethod String where
    convert Cash           = "Paiement en espèces"
    convert Card           = "Paiement par carte bancaire"
    convert Cryptocurrency = "Paiement en cryptomonnaie"
```

* Ici, `a` = `PaymentMethod` et `b` = `String`.
* Chaque constructeur de `PaymentMethod` est converti en une phrase descriptive.

---

#### 4. **Fonction `main` pour tester**

```haskell
main :: IO ()
main = do
    putStrLn ("Cash → " ++ convert Cash)
    putStrLn ("Card → " ++ convert Card)
    putStrLn ("Cryptocurrency → " ++ convert Cryptocurrency)
```

* On affiche le résultat de `convert` appliqué à chaque valeur du type `PaymentMethod`.

---

### **Sortie attendue dans le terminal :**

```
Cash → Paiement en espèces
Card → Paiement par carte bancaire
Cryptocurrency → Paiement en cryptomonnaie
```

---
