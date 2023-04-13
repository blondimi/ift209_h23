_En construction..._

# D'un caractère hexadécimal vers sa valeur numérique

Supposons que `w19` contienne le code ASCII d'un caractère parmi {`0`, ..., `9`, `A`, ..., `F`}.
Voyons comment obtenir la valeur numérique du caractère dans `w20`. Par exemple, `C` doit devenir 12. 

## 0 à 9

Les caractrères `0` à `9` sont représentés comme suit:

| Caractère | Code décimal | Code binaire |
|---|---|---|
|`0`|48|00110000|
|`1`|49|00110001|
|`2`|50|00110010|
|`3`|51|00110011|
|`4`|52|00110100|
|`5`|53|00110101|
|`6`|54|00110110|
|`7`|55|00110111|
|`8`|56|00111000|
|`9`|57|00111001|

Remarquons que les quatre bits de poids faible du code binaire correspondent exactement à la valeur numérique du chiffre.
Par exemple, `9` est représenté par 0011**1001** et vaut en effet 1001₂ = 9. Ainsi, la valeur numérique peut être obtenue avec:

```
and  w20, w19, 0x0F
```

# A à F

Les caractrères `A` à `F` sont représentés comme suit:

| Caractère | Code décimal | Code binaire |
|---|---|---|
|`A`|65|01000001|
|`B`|66|01000010|
|`C`|67|01000011|
|`D`|68|01000100|
|`E`|69|01000101|
|`F`|70|01000110|

Remarquons que les quatre bits de poids faible du code binaire correspondent à la valeur numérique du chiffre déphasée de 9.
Par exemple, `F` est représenté par 0100**0110** et vaut en effet 0110₂ + 9 = 6 + 9 = 15. Ainsi, la valeur numérique peut être obtenue avec:

```
and  w20, w19, 0x0F
add  w20, w20, 0x09
```
