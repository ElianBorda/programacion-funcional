# Practica

**Ejercicio 1**

*Dadas las siguientes definiciones*
```haskell
data Gusto = Chocolate | DulceDeLeche | Frutilla | Sambayon
data Helado = Vasito Gusto
            | Cucurucho Gusto Gusto
            | Pote Gusto Gusto Gusto
chocoHelate consH = consH Chocolate
```

*determinar el tipo de las siguientes expresiones:*
1. Vasito
2. Chocolate
3. Cucurucho
4. Sambayon
5. Pote
6. chocoHelate
7. chocoHelate Vasito
8. chocoHelate Cucurucho
9. chocoHelate (Cucurucho Sambayon)
10. chocoHelate (chocoHelate Cucurucho)
11. chocoHelate (Vasito DulceDeLeche)
12. chocoHelate Pote
13. chocoHelate (chocoHelate (Pote Frutilla))

_Solucion:_

1. `Gusto->Helado`
2. `Gusto`
3. `Gusto->Gusto->Helado`
4. `Gusto`
5. `Gusto->Gusto->Gusto->Helado`
6. `(Gusto->Helado)->Helado`
7. `Helado`
8. `Sin tipo`
9. `Helado`
10. `Helado`    
11. `Sin tipo`
12. `Sin tipo`
13. `Sin tipo`

**En duda**: ¿Helado debe recibir el los dos gustos de primeras, o no pasa nada si recibe de a uno?


**Ejercicio 2**

*Dado el siguiente tipo que pretende representar dígitos binarios*
```haskell
data DigBin = O | I
```

*definir las siguientes funciones:*
1. `dbAsInt::DigBin->Int`, que dado un símbolo que representa un dígito binario lo transforma en su significado como número.
2. `dbAsBool::DigBin->Bool`, que dado un símbolo que representa un dígito binario lo transforma en su significado como booleano
3. `dbOfBool::Bool->DigBin` ,que dado un booleano lo transforma en el símbolo que representa a ese booleano.
4. `negDB::DigBin->DigBin`, que dado un dígito binario lo transforma en el otro.

_Solucion:_

1. 
    ```haskell
    dbAsInt::DigBin->Int
    dbAsInt I = 1
    dbAsInt O = 0
    ```

2. 
    ```haskell
    dbAsBool::DigBin->Bool
    dbAsBool I = True
    dbAsBool O = False
    ```

3. 
    ```haskell
    dbOfBool::Bool->DigBin
    dbOfBool True  = I
    dbOfBool False = O
    ```

4. 
    ```haskell
    negDB::DigBin->DigBin
    negDB I = O
    negDB O = I
    ```