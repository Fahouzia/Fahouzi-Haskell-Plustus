E**HC11T9 : Type `Length` avec unités (mètres et kilomètres)**.

---

## 🔹 Énoncé

> Définir un nouveau type `Length` avec les constructeurs `M` et `Km`, dériver `Eq`,
et corriger manuellement les comparaisons entre mètres et kilomètres.

---

## 🔹 Code 

```haskell
-- Définition du type Length avec deux unités : mètres et kilomètres
data Length = M Double | Km Double
  deriving (Show, Eq)

-- Instance Ord manuelle pour comparer correctement M et Km
instance Ord Length where
  compare (M x) (M y) = compare x y                          -- mètres vs mètres
  compare (Km x) (Km y) = compare x y                        -- km vs km
  compare (M x) (Km y) = compare x (y * 1000)                -- conversion km → m
  compare (Km x) (M y) = compare (x * 1000) y                -- conversion km → m

-- Fonction main pour tester
main :: IO ()
main = do
  let l1 = M 500
  let l2 = Km 1
  let l3 = M 2000
  let l4 = Km 0.5

  putStrLn ("l1 : " ++ show l1)
  putStrLn ("l2 : " ++ show l2)
  putStrLn ("l3 : " ++ show l3)
  putStrLn ("l4 : " ++ show l4)

  putStrLn ("\nl1 < l2 ? " ++ show (l1 < l2))   -- True, 500 m < 1000 m
  putStrLn ("l3 > l2 ? " ++ show (l3 > l2))     -- True, 2000 m > 1000 m
  putStrLn ("l4 == l2 ? " ++ show (l4 == l2))   -- False, car Eq n’est pas converti automatiquement
  putStrLn ("Comparaison l4 et l2 : " ++ show (compare l4 l2))  -- LT, car 500 m < 1000 m
```

---

## 🔹 Explication pas à pas

1. **Définition du type `Length` :**

   ```haskell
   data Length = M Double | Km Double
   ```

   Ce type permet de représenter des longueurs soit en **mètres (M)**, soit en **kilomètres (Km)**.

2. **Dérivation de `Eq` :**

   ```haskell
   deriving (Show, Eq)
   ```

   Cela permet :

   * d’afficher facilement les longueurs ;
   * de comparer directement des longueurs **avec le même constructeur** (ex. `M 10 == M 10`).

   ⚠️ Mais **`Eq` dérivé** ne compare pas `M 1000` et `Km 1` comme égaux — d’où la nécessité d’un `Ord` personnalisé.

3. **Implémentation manuelle de `Ord` :**
   On veut que :

   * `M 1000 == Km 1` → considérés égaux en comparaison d’ordre.
   * `M 500 < Km 1` → car 500 m < 1000 m.
   * `Km 2 > M 1500` → car 2000 m > 1500 m.

   Pour cela :

   ```haskell
   compare (M x) (Km y) = compare x (y * 1000)
   compare (Km x) (M y) = compare (x * 1000) y
   ```

   On convertit **tout en mètres** avant de comparer.

4. **Tests :**

   * `l1 = M 500`
   * `l2 = Km 1`
   * `l3 = M 2000`
   * `l4 = Km 0.5`

   → Les comparaisons donnent des résultats logiques.

---

## 🔹 Exemple de sortie

```
l1 : M 500.0
l2 : Km 1.0
l3 : M 2000.0
l4 : Km 0.5

l1 < l2 ? True
l3 > l2 ? True
l4 == l2 ? False
Comparaison l4 et l2 : LT
```
