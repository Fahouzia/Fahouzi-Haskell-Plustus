HC3T6 - Tâche avancée 6 : Vérifier une année bissextile avec if-then-else

```haskell
-- HC3T6 - Tâche avancée 6 : Vérifier une année bissextile avec if-then-else

isLeapYear :: Int -> Bool
isLeapYear year =
    if year `mod` 400 == 0 then True
    else if year `mod` 100 == 0 then False
    else if year `mod` 4 == 0 then True
    else False

main :: IO ()
main = do
    putStrLn "=== Vérification d'années bissextiles ==="
    putStrLn ("2000 : " ++ show (isLeapYear 2000))
    putStrLn ("1900 : " ++ show (isLeapYear 1900))
    putStrLn ("2024 : " ++ show (isLeapYear 2024))
    putStrLn ("2023 : " ++ show (isLeapYear 2023))
```

---

##  **Explication détaillée**

###  1. Le commentaire

```haskell
-- HC3T6 - Tâche avancée 6 : Vérifier une année bissextile avec if-then-else
```

C’est juste une **ligne de commentaire** (le double tiret `--` indique un commentaire).
Elle n’est pas exécutée, elle sert à **décrire** ce que fait le programme.

---

###  2. La signature de la fonction

```haskell
isLeapYear :: Int -> Bool
```

Cela veut dire que la fonction `isLeapYear` :

* prend un **entier (`Int`)** en entrée,
* et retourne une **valeur booléenne (`Bool`)** (`True` ou `False`).

---

###  3. Le corps de la fonction

```haskell
isLeapYear year =
    if year `mod` 400 == 0 then True
    else if year `mod` 100 == 0 then False
    else if year `mod` 4 == 0 then True
    else False
```

#### Étape par étape :

* `year \`mod` 400 == 0`→ Si l’année est divisible par **400**, elle est **bissextile**.  
  Exemple : 2000 → ✅`True`

* `year \`mod` 100 == 0`→ Si elle est divisible par **100** mais **pas par 400**,  
  elle n’est **pas bissextile**.  
  Exemple : 1900 → ❌`False`

* `year \`mod` 4 == 0`→ Si elle est divisible par **4**, elle est **bissextile**.  
  Exemple : 2024 → ✅`True`

* Sinon (`else False`), ce n’est **pas une année bissextile**.
  Exemple : 2023 → ❌ `False`

---

### 4. La fonction `main`

```haskell
main :: IO ()
```

 Elle définit le **point d’entrée** du programme.
C’est la première fonction exécutée quand tu lances le programme.

---

### 5. Le bloc `do`

```haskell
main = do
    putStrLn "=== Vérification d'années bissextiles ==="
    putStrLn ("2000 : " ++ show (isLeapYear 2000))
    putStrLn ("1900 : " ++ show (isLeapYear 1900))
    putStrLn ("2024 : " ++ show (isLeapYear 2024))
    putStrLn ("2023 : " ++ show (isLeapYear 2023))
```

#### Détail :

* `putStrLn` affiche du texte à l’écran.
* `"2000 : " ++ show (isLeapYear 2000)` concatène le texte `"2000 : "`
  avec le **résultat converti en texte** (`show` transforme un `Bool` en `"True"` ou `"False"`).

---

###  6. Résultat à l’exécution

```
=== Vérification d'années bissextiles ===
2000 : True
1900 : False
2024 : True
2023 : False
```
