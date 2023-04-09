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

