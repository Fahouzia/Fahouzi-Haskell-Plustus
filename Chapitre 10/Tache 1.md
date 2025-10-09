HC10T1 : Classe de type ShowSimple

```haskell
-- Définition de la classe ShowSimple
class ShowSimple a where
    showSimple :: a -> String

-- Définition du type PaymentMethod
data PaymentMethod = Cash | CreditCard | DebitCard

-- Instance de ShowSimple pour PaymentMethod
instance ShowSimple PaymentMethod where
    showSimple Cash       = "Cash"
    showSimple CreditCard = "Credit Card"
    showSimple DebitCard  = "Debit Card"

-- Fonction main pour tester showSimple
main :: IO ()
main = do
    let pm1 = Cash
    let pm2 = CreditCard
    let pm3 = DebitCard
    putStrLn $ showSimple pm1
    putStrLn $ showSimple pm2
    putStrLn $ showSimple pm3
```

---

### Explication ligne par ligne

1. ```haskell
   class ShowSimple a where
       showSimple :: a -> String
   ```

   * On crée une **classe de type** `ShowSimple`.
   * Tout type `a` qui devient instance de `ShowSimple` doit fournir une fonction `showSimple` qui convertit une valeur en chaîne de caractères.

2. ```haskell
   data PaymentMethod = Cash | CreditCard | DebitCard
   ```

   * On définit un **type énuméré** `PaymentMethod` avec trois valeurs possibles : `Cash`, `CreditCard`, `DebitCard`.

3. ```haskell
   instance ShowSimple PaymentMethod where
       showSimple Cash       = "Cash"
       showSimple CreditCard = "Credit Card"
       showSimple DebitCard  = "Debit Card"
   ```

   * On rend `PaymentMethod` une instance de `ShowSimple`.
   * Pour chaque constructeur (`Cash`, `CreditCard`, `DebitCard`), on définit comment le représenter sous forme de chaîne de caractères.

4. ```haskell
   main :: IO ()
   main = do
       let pm1 = Cash
       let pm2 = CreditCard
       let pm3 = DebitCard
       putStrLn $ showSimple pm1
       putStrLn $ showSimple pm2
       putStrLn $ showSimple pm3
   ```

   * `main` crée trois valeurs de type `PaymentMethod`.
   * `putStrLn $ showSimple pmX` affiche la version simple de chaque paiement.
   * Résultat attendu à l’exécution :

     ```
     Cash
     Credit Card
     Debit Card
     ```

---
