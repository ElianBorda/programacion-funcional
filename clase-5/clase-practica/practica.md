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
1. `dbAsInt :: DigBin -> Int`, que dado un símbolo que representa un dígito binario lo transforma en su significado como número.
2. `dbAsBool :: DigBin -> Bool`, que dado un símbolo que representa un dígito binario lo transforma en su significado como booleano
3. `dbOfBool :: Bool -> DigBin` ,que dado un booleano lo transforma en el símbolo que representa a ese booleano.
4. `negDB :: DigBin -> DigBin`, que dado un dígito binario lo transforma en el otro.

_Solucion:_

1. 
    ```haskell
    dbAsInt :: DigBin -> Int
    dbAsInt I = 1
    dbAsInt O = 0
    ```

2. 
    ```haskell
    dbAsBool :: DigBin -> Bool
    dbAsBool I = True
    dbAsBool O = False
    ```

3. 
    ```haskell
    dbOfBool :: Bool -> DigBin
    dbOfBool True  = I
    dbOfBool False = O
    ```

4. 
    ```haskell
    negDB :: DigBin -> DigBin
    negDB I = O
    negDB O = I
    ```


**Ejercicio 3**

*Dado el siguiente tipo que pretende representar dígitosdecimales*
```haskell
data DigDec = D0 | D1 | D2 | D3 | D4 
            | D5 | D6 | D7 | D8 | D9
```

*definir las siguientes funciones:*
1. `ddAsInt :: DigDec -> Int`, que dado un símbolo que representa un dígito decimal lo transforma en su significado como número.
2. `ddOfInt :: Int -> DigDec`, que dado un número entre 0 y 9 lo transforma en el símbolo que representa a ese dígito.
3. `nextDD :: DigDec -> DigDec`, que dado un dígito decimal lo transforma en el siguiente según el orden circular dado en la definición.
4. `prevDD :: DigDec -> DigDec`, que dado un dígito decimal lo transforma en el anterior según el orden circular dado en la definición.

_Solucion:_

1. 
    ```haskell
    ddAsInt :: DigDec -> Int
    ddAsInt D0 = 0
    ddAsInt D1 = 1
    ddAsInt D2 = 2
    ddAsInt D3 = 3
    ddAsInt D4 = 4
    ddAsInt D5 = 5
    ddAsInt D6 = 6
    ddAsInt D7 = 7
    ddAsInt D8 = 8
    ddAsInt D9 = 9
    ```

2. 
    ```haskell
    ddOfInt :: Int -> DigDec
    ddOfInt 0 = D0
    ddOfInt 1 = D1
    ddOfInt 2 = D2
    ddOfInt 3 = D3
    ddOfInt 4 = D4
    ddOfInt 5 = D5
    ddOfInt 6 = D6
    ddOfInt 7 = D7
    ddOfInt 8 = D8
    ddOfInt 9 = D9
    ```

3. 
    ```haskell
    nextDD :: DigDec -> DigDec
    nextDD D9 = error "No tiene siguiente"
    nextDD d = ddOfInt ((ddAsInt d)+1)
    ```

4. 
    ```haskell
    prevDD :: DigDec -> DigDec
    prevDD D0 = error "No tiene anterior"
    prevDD d = ddOfInt ((ddAsInt d)-1)
    ```

**Ejercicio 4**

*Dado el siguiente tipo que representa medidas en un software de dibujo como LibreOffice Draw.*
```haskell
data Medida = Mm Float | Cm Float 
            | Inch Float | Foot Float
```

*y la siguiente tabla de conversión*
|          | **Mm**    | **Cm**    | **Inch**  | **Foot**  |
|------|-------|-------|-------|-------|
|  **Mm**  | 1     | 0.1   | 0.039 | 0.003 |
|  **Cm**  | 10    | 1     | 0.394 | 0.033 |
| **Inch** | 25.4  | 2.54  | 1     | 0.083 |
| **Foot** | 304.8 | 30.48 | 12    | 1     |

*escribir las siguientes funciones:*
1. `asMm :: Medida -> Medida`, que dada una medida cualquiera la transforma en una medida en milímetros que aproxima la dada según la conversión establecida.

2. `asCm :: Medida -> Medida`, que dada una medida cualquiera la transforma en una medida en centímetros que aproxima la dada según la conversión establecida.

3. `asInch :: Medida -> Medida`, que dada una medida cualquiera la transforma en una medida en pulgadas que aproxima la dada según la conversión establecida.

4. `asFoot :: Medida -> Medida`, que dada una medida cualquiera la transforma en una medida en pies que aproxima la dada según la conversión establecida.

_Solucion:_

1. 
```haskell 
asMm :: Medida -> Medida
asMm (Cm f)   = Mm (f*10)
asMm (Inch f) = Mm (f*25.4)
asMm (Foot f) = Mm (f*304.8)
asMm (Mm f)   = Mm f
```

2. 
```haskell 
asCm :: Medida -> Medida
asCm (Mm f)   = Cm (f*0.1)
asCm (Inch f) = Cm (f*2.54)
asCm (Foot f) = Cm (f*30.48)
asCm (Cm f)   = Cm f
```

3. 
```haskell 
asInch :: Medida -> Medida
asInch (Mm f)   = Inch (f*0.039)
asInch (Cm f)   = Inch (f*0.394)
asInch (Foot f) = Inch (f*12)
asInch (Inch f) = Inch f
```

4. 
```haskell
asFoot :: Medida -> Medida
asFoot (Mm f)   = Foot (f*0.003)
asFoot (Cm f)   = Foot (f*0.033)
asFoot (Inch f) = Foot (f*0.083)
asFoot (Foot f) = Foot f
```

**Ejercicio 5**

*Dadas las siguientes definiciones:*
```haskell
data Shape = Circle Float | Rect Float Float

construyeShNormal :: (Float -> Shape) -> Shape
construyeShNormal c = c 1.0
```

*Determinar el tipo de las siguientes expresiones:*

1. `uncurry Rect` 
2. `construyeShNormal (flip Rect 5.0)` 
3. `compose (uncurry Rect) swap` 
4. `uncurry Cucurucho` 
5. `uncurry Rect swap` 
6. `compose uncurry Pote` 
7. `compose Just` 
8. `compose uncurry (Pote Chocolate)` 