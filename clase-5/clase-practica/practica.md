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