HC11T8 : Dérivation de Eq et Ord pour PaymentMethod

## 🔹 Énoncé

> Dériver les instances `Eq` et `Ord` pour le type `PaymentMethod` et tester les comparaisons.

---

##  Code

```haskell
-- Définition du type PaymentMethod
data PaymentMethod = Cash | Card | Cryptocurrency
  deriving (Show, Eq, Ord)

-- Fonction main pour tester les comparaisons
main :: IO ()
main = do
  let p1 = Cash
  let p2 = Card
  let p3 = Cryptocurrency
  let p4 = Cash

  putStrLn ("p1 == p2 : " ++ show (p1 == p2))       -- False
  putStrLn ("p1 == p4 : " ++ show (p1 == p4))       -- True
  putStrLn ("p1 < p2 : " ++ show (p1 < p2))         -- True (ordre de déclaration)
  putStrLn ("p3 > p2 : " ++ show (p3 > p2))         -- True
  putStrLn ("Comparaison complète : " ++ show (compare p2 p3))  -- LT car Card < Cryptocurrency
```

---

## 🔹 Explication pas à pas

1. **Définition du type :**

   ```haskell
   data PaymentMethod = Cash | Card | Cryptocurrency
   ```

   → On définit un type énuméré avec trois méthodes de paiement possibles.

2. **Dérivation automatique :**

   ```haskell
   deriving (Show, Eq, Ord)
   ```

   Cela indique à Haskell de **générer automatiquement** :

   * `Show` → pour pouvoir afficher (`print`, `show`)
   * `Eq` → pour comparer l’égalité (`==`, `/=`)
   * `Ord` → pour comparer l’ordre (`<`, `>`, `<=`, `>=`, `compare`)

3. **Ordre de comparaison (`Ord`) :**
   L’ordre est **déterminé par la position des constructeurs** dans la déclaration :

   ```
   Cash < Card < Cryptocurrency
   ```

4. **Tests :**

   * `Cash == Card` → `False`
   * `Cash == Cash` → `True`
   * `Cash < Card` → `True`
   * `Cryptocurrency > Card` → `True`

---

## 🔹 Exemple de sortie

```
p1 == p2 : False
p1 == p4 : True
p1 < p2 : True
p3 > p2 : True
Comparaison complète : LT
```

---
