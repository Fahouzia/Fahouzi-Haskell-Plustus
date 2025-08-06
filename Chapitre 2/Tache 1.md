HC2T1 - Tâche 1 : Vérification des types dans GHCi

Dans le  terminal:

```bash
ghci
```

`command not found`, c’est que **GHCi n’est pas installé.
si c'est pas installé on install **Haskell Platform** ou **GHC + GHCi**. 
su obuntu :
```bash
sudo apt update
sudo apt install ghc

Puis réessaie :

```bash
ghci


Étape 2 : Vérifier une expression simple

Une fois dans GHCi (tu verras quelque chose comme `Prelude>`), tape :

```haskell
:t 42
```


# Exemple

```bash
$ ghci
GHCi, version ...
Prelude> :t 42
42 :: Num a => a    -- Cela signifie que 42 peut être de n'importe quel type numérique (générique)

Prelude> :t 3.14
3.14 :: Fractional a => a

Prelude> :t "Haskell"
"Haskell" :: [Char]

Prelude> :t 'Z'
'Z' :: Char

Prelude> :t True && False
True && False :: Bool



