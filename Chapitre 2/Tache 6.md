HC2T6 - Tâche 6 : Comprendre Int vs Integer

CODE 

```haskell
-- Définition de variables avec des types différents

smallNumber :: Int
smallNumber = 262

bigNumber :: Integer
bigNumber = 2127
```

---

QUELQUES DIFFERENCE ENTRE INT ET INTEGER 
| Type      | Taille                    | Limite                                          | Remarques                             |
| --------- | ------------------------- | ----------------------------------------------- | ------------------------------------- |
| `Int`     | Taille **fixe** (machine) | En général de `-2^63` à `2^63 - 1` (en 64 bits) | Plus rapide, mais limité              |
| `Integer` | Taille **illimitée**      | Aucune limite théorique                         | Plus lent, mais peut grandir sans fin |

---

EFFECTUONS LE TEST 

Dans ton terminal :

```bash
ghci
```

Puis tape :

```haskell
2^64 :: Int
```

Tu obtiendras **une erreur ou un dépassement (overflow)**, car `2^64 = 18446744073709551616` 
dépasse la capacité maximale de `Int` sur la plupart des machines (en 64 bits, `Int` va jusqu’à `2^63 - 1`).

---

 Solution correcte :

Essaye ceci à la place :

```haskell
2^64 :: Integer
```

Et là, **ça fonctionne**, car `Integer` peut stocker des nombres très grands sans limite.

---

EXEMPLE 

```haskell
Prelude> 2^64 :: Int
-- *** Exception: arithmetic overflow

Prelude> 2^64 :: Integer
18446744073709551616
```

---

* On  Utilise `Int` si tu as besoin de performance et que tu es sûr que les valeurs restent petites.
*On Utilise `Integer` si tu manipules **des grands nombres** (comme des puissances, des calculs mathématiques complexes).
