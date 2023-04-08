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

a. Vasito
b. Chocolate
c. Cucurucho
d. Sambayon
e. Pote
f. chocoHelate
g. chocoHelate Vasito
h. chocoHelate Cucurucho
i. chocoHelate (Cucurucho Sambayon)
j. chocoHelate (chocoHelate Cucurucho)
k. chocoHelate (Vasito DulceDeLeche)
l. chocoHelate Pote
m. chocoHelate (chocoHelate (Pote Frutilla))