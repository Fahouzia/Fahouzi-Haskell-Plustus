HC10T3 : Classe de type Comparable

### **Code:**

```haskell
-- HC10T3 : Classe de type Comparable

-- Définition de la classe Comparable
class Comparable a where
    compareWith :: a -> a -> Ordering

-- Définition d'un type Blockchain
data Blockchain = Blockchain {
    name :: String,
    blocks :: Int
} deriving (Show)

-- Implémentation de la classe Comparable pour Blockchain
instance Comparable Blockchain where
    compareWith b1 b2
        | blocks b1 < blocks b2 = LT
        | blocks b1 > blocks b2 = GT
        | otherwise              = EQ

-- Fonction principale pour tester
main :: IO ()
main = do
    let btc = Blockchain "Bitcoin" 800000
    let eth = Blockchain "Ethereum" 600000
    let bnb = Blockchain "BNB Chain" 800000

    putStrLn ("Comparaison BTC vs ETH : " ++ show (compareWith btc eth))
    putStrLn ("Comparaison ETH vs BTC : " ++ show (compareWith eth btc))
    putStrLn ("Comparaison BTC vs BNB : " ++ show (compareWith btc bnb))
```

---

###  **Explication pas à pas :**

1. **Création de la classe `Comparable` :**

   ```haskell
   class Comparable a where
       compareWith :: a -> a -> Ordering
   ```

   * Cela définit une **classe de type** appelée `Comparable`.
   * Tout type qui appartient à cette classe doit implémenter une fonction `compareWith` qui compare deux valeurs et retourne un résultat de type `Ordering` :

     * `LT` = *Less Than* (plus petit),
     * `GT` = *Greater Than* (plus grand),
     * `EQ` = *Equal* (égal).

2. **Définition du type `Blockchain` :**

   ```haskell
   data Blockchain = Blockchain {
       name :: String,
       blocks :: Int
   } deriving (Show)
   ```

   * Ce type représente une blockchain avec :

     * un nom (`name`) de type `String`,
     * un nombre de blocs (`blocks`) de type `Int`.

3. **Implémentation de la classe pour `Blockchain` :**

   ```haskell
   instance Comparable Blockchain where
       compareWith b1 b2
           | blocks b1 < blocks b2 = LT
           | blocks b1 > blocks b2 = GT
           | otherwise              = EQ
   ```

   * Ici, on compare deux blockchains **selon leur nombre de blocs**.
   * Si `b1` a plus de blocs que `b2`, elle est considérée plus grande.

4. **Programme principal (`main`) :**

   * On crée trois blockchains : `btc`, `eth`, `bnb`.
   * On compare les paires avec `compareWith` et on affiche le résultat :

     ```haskell
     putStrLn ("Comparaison BTC vs ETH : " ++ show (compareWith btc eth))
     ```
   * Le résultat (`Ordering`) est affiché grâce à `show`.

---

###  **Exécution et sortie attendue :**

```
Comparaison BTC vs ETH : GT
Comparaison ETH vs BTC : LT
Comparaison BTC vs BNB : EQ
```

---

Souhaites-tu que je t’ajoute aussi une **version améliorée** où la comparaison prend en compte **à la fois le nombre de blocs et le nom** en cas d’égalité (comme une vraie comparaison lexicographique) ?
