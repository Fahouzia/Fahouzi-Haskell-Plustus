HC8T9 : Type enregistrement Transaction et fonction associée
---

###  à faire

> Définir un type `Transaction` avec les champs :
>
> * `from :: Address`
> * `to :: Address`
> * `amount :: Value`
> * `transactionId :: String`
>
> Définir une fonction
> `createTransaction :: Address -> Address -> Value -> String`
> qui crée une transaction et retourne **l’ID de la transaction**.

---

###  Code 
```haskell
-- HC8T9.hs

-- Définition de synonymes de type
type Address = String
type Value   = Int

-- Définition du type Transaction avec la syntaxe d’enregistrement
data Transaction = Transaction
  { from          :: Address
  , to            :: Address
  , amount        :: Value
  , transactionId :: String
  } deriving (Show)

-- Fonction pour créer une transaction et retourner son ID
createTransaction :: Address -> Address -> Value -> String
createTransaction fromAddr toAddr val =
    let txId = fromAddr ++ "_" ++ toAddr ++ "_" ++ show val
        transaction = Transaction { from = fromAddr, to = toAddr, amount = val, transactionId = txId }
    in transactionId transaction  -- on retourne uniquement l'ID

-- Fonction principale pour tester
main :: IO ()
main = do
    let fromAddr = "Alice123"
    let toAddr   = "Bob456"
    let val      = 250
    let txId     = createTransaction fromAddr toAddr val
    putStrLn ("ID de la transaction : " ++ txId)
```

---

###  Explication

1. **`type Address = String` et `type Value = Int`**

   * On crée des synonymes de type pour rendre le code plus lisible :

     * Une adresse (`Address`) est une chaîne.
     * Une valeur (`Value`) est un entier.

2. **Définition du type `Transaction`**

   ```haskell
   data Transaction = Transaction
     { from :: Address
     , to :: Address
     , amount :: Value
     , transactionId :: String
     } deriving (Show)
   ```

   * On utilise la **syntaxe d’enregistrement** (`{ ... }`) pour nommer les champs.
   * Le `deriving (Show)` permet d’afficher facilement une transaction.

3. **Fonction `createTransaction`**

   ```haskell
   createTransaction fromAddr toAddr val =
       let txId = fromAddr ++ "_" ++ toAddr ++ "_" ++ show val
           transaction = Transaction { from = fromAddr, to = toAddr, amount = val, transactionId = txId }
       in transactionId transaction
   ```

   * On crée un **ID unique** en combinant les adresses et le montant.
   * On construit un enregistrement `Transaction`.
   * On retourne **seulement l’ID** de la transaction.

4. **`main`**

   * On définit deux adresses et un montant.
   * On appelle `createTransaction` et on affiche l’ID obtenu.

---

###  Exemple de sortie

```
ID de la transaction : Alice123_Bob456_250
```

---
