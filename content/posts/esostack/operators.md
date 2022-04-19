+++
title = "Operators"
date = "2022-02-19"
tags = ['EsoStack', 'Coding', 'Docs', 'EsoLangs']
description = " "
+++

---

## Arithmetic

### Add

_Descirption:_ Sum the top 2 elements

_Args:_ 2

_Tokens:_ +

_Example:_

```
|...|b|a| -> |...|a + b|
```

### Subtract

_Descirption:_ Subtract the top 2 elements

_Args:_ 2

_Example:_ -

```
|...|b|a| -> |...|a - b|
```

### Multiply

_Descirption:_ Multiply the top 2 elements

_Args:_ 2

_Tokens:_ \*

_Example:_

```
|...|b|a| -> |...|a * b|
```

### Divide

_Descirption:_ Divide the top 2 elements

_Args:_ 2

_Tokens:_ /

_Example:_

```
|...|b|a| -> |...|a / b|
```

### Modulus

_Descirption:_ Get the rest of the division of the top 2 elements

_Args:_ 2

_Tokens:_ %

_Example:_

```
|...|b|a| -> |...|a % b|
```

### Power

_Descirption:_ Get the top element to the power of the second

_Args:_ 2

_Tokens:_ ^

_Example:_

```
|...|b|a| -> |...|a ^ b|
```

---

## Logic

### And

_Descirption:_ Logical And with the top 2 elements

_Args:_ 2

_Tokens:_ &&, and

_Example:_

```
|...|1|1| -> |...|1|
|...|0|1| -> |...|0|
|...|1|0| -> |...|0|
|...|0|0| -> |...|0|
```

### Or

_Descirption:_ Logical Or with the top 2 elements

_Args:_ 2

_Tokens:_ ||, or

_Example:_

```
|...|1|1| -> |...|1|
|...|0|1| -> |...|1|
|...|1|0| -> |...|1|
|...|0|0| -> |...|0|
```

### Xor

_Descirption:_ Logical Exclusive Or with the top 2 elements

_Args:_ 2

_Tokens:_ XX, xor

_Example:_

```
|...|1|1| -> |...|0|
|...|0|1| -> |...|1|
|...|1|0| -> |...|1|
|...|0|0| -> |...|0|
```

### Not

_Descirption:_ Logical Negation with the top element

_Args:_ 1

_Tokens:_ !!, not

_Example:_

```
|...|1| -> |...|0|
|...|5| -> |...|0|
|...|0| -> |...|1|
```

---

## Comparison

### Lesser

_Descirption:_ Check if the top element is < than the second one

_Args:_ 2

_Tokens:_ <

_Example:_

```
|...|1|5| -> |...|5 < 1| -> |...|0|
|...|5|1| -> |...|1 < 5| -> |...|1|
|...|5|5| -> |...|5 < 5| -> |...|0|

```

### Lesser or Equal

_Descirption:_ Check if the top element is ≤ than the second one

_Args:_ 2

_Tokens:_ <=

_Example:_

```
|...|1|5| -> |...|5 <= 1| -> |...|0|
|...|5|1| -> |...|1 <= 5| -> |...|1|
|...|5|5| -> |...|5 <= 5| -> |...|1|
```

### Greater

_Descirption:_ Check if the top element is > than the second one

_Args:_ 2

_Tokens:_ >

_Example:_

```
|...|1|5| -> |...|5 > 1| -> |...|1|
|...|5|1| -> |...|1 > 5| -> |...|0|
|...|5|5| -> |...|5 > 5| -> |...|0|
```

### Greater or Equal

_Descirption:_ Check if the top element is ≥ than the second one

_Args:_ 2

_Tokens:_ >=

_Example:_

```
|...|1|5| -> |...|5 >= 1| -> |...|1|
|...|5|1| -> |...|1 >= 5| -> |...|0|
|...|5|5| -> |...|5 >= 5| -> |...|1|
```

### Equal

_Descirption:_ Check if the top 2 elements are equal

_Args:_ 2

_Tokens:_ ==

_Example:_

```
|...|1|5| -> |...|5 == 1| -> |...|0|
|...|5|5| -> |...|5 == 5| -> |...|1|
```

### Different

_Descirption:_ Check if the top 2 elements are different

_Args:_ 2

_Tokens:_ !=

_Example:_

```
|...|1|5| -> |...|5 != 1| -> |...|1|
|...|5|5| -> |...|5 != 5| -> |...|0|
```
