HC6T2 – Suite de Fibonacci (récursif)

```haskell
-- HC6T2 : Suite de Fibonacci (récursif)
-- Exemple : calcul de fibonacci 4

fibonacci :: Integer -> Integer
fibonacci n
    | n < 0     = error "La suite de Fibonacci n’est pas définie pour les nombres négatifs."
    | n == 0    = 0
    | n == 1    = 1
    | otherwise = fibonacci (n - 1) + fibonacci (n - 2)

main :: IO ()
main = do
    let n = 4                            -- exemple : on calcule fibonacci 4
    let result = fibonacci n             -- appel de la fonction
    putStrLn ("Le " ++ show n ++ "ᵉ nombre de Fibonacci est : " ++ show result)
```

---

## **Explication claire**

### 🔹 Étape 1 — Cas de base

* `fibonacci 0 = 0`
* `fibonacci 1 = 1`

### 🔹 Étape 2 — Cas récursif

Pour tout `n > 1` :

```haskell
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)
```

La fonction **s'appelle elle-même** deux fois jusqu’à atteindre les cas de base.

---

## **Exécution pas à pas pour `n = 4`**

```
fibonacci 4
= fibonacci 3 + fibonacci 2
= (fibonacci 2 + fibonacci 1) + (fibonacci 1 + fibonacci 0)
= ((fibonacci 1 + fibonacci 0) + 1) + (1 + 0)
= ((1 + 0) + 1) + (1 + 0)
= (1 + 1) + 1
= 2 + 1
= 3
```md
```

---

## 🖥️ **Comment exécuter**

Dans ton terminal (fichier `Main.hs`) :

```bash
runhaskell Main.hs
```

**Sortie affichée :**

```
Le 4ᵉ nombre de Fibonacci est : 3
```

---


La suite de Fibonacci est définie par :

```
F(0) = 0  
F(1) = 1  
F(n) = F(n-1) + F(n-2)   pour n > 1
```

---


---


* **Cas d’erreur :**
  Si `n` est négatif → message d’erreur.

* **Cas de base :**

  * `fibonacci 0 = 0`
  * `fibonacci 1 = 1`

* **Cas récursif :**
  Pour `n > 1`, on additionne les deux précédents termes :

  ```haskell
  fibonacci (n - 1) + fibonacci (n - 2)
  ```

---

### Exemple d’exécution

Calculons `fibonacci 5` :

```
fibonacci 5
= fibonacci 4 + fibonacci 3
= (fibonacci 3 + fibonacci 2) + (fibonacci 2 + fibonacci 1)
= ((fibonacci 2 + fibonacci 1) + (fibonacci 1 + fibonacci 0)) + ((fibonacci 1 + fibonacci 0) + 1)
= ((1 + 1) + (1 + 0)) + ((1 + 0) + 1)
= (2 + 1) + (1 + 1)
= 3 + 2
= 5
```
---

### 🧪 Tests

```haskell
fibonacci 0   -- 0
fibonacci 1   -- 1
fibonacci 5   -- 5
fibonacci 8   -- 21
fibonacci (-3) -- Erreur : La suite de Fibonacci n’est pas définie pour les nombres négatifs.
```
