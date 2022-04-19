+++
title = "Functions"
date = "2022-02-19"
tags = ['EsoStack', 'Coding', 'Docs', 'EsoLangs']
description = " "
+++

---

## Stack

### Swap

_Descirption:_ Swap the order of the first 2 elements

_Args:_ 2

_Tokens:_ swap

_Example:_

```
|...|b|a| -> |...|a|b|
```

### Dup

_Descirption:_ Duplicate the top element

_Args:_ 1

_Tokens:_ dup

_Example:_

```
|...|b|a| -> |...|b|a|a|
```

### Dup2

_Descirption:_ Duplicate the top 2 elements

_Args:_ 2

_Tokens:_ dup2

_Example:_

```
|...|b|a| -> |...|b|a|b|a|
```

### Duplicate

_Descirption:_ Duplicate the whole stack

_Args:_ 0

_Tokens:_ duplicate

_Example:_

```
|c|...|b|a| -> |c|...|b|a|c|...|b|a
```

### Drop

_Descirption:_ Remove the top element

_Args:_ 1

_Tokens:_ drop

_Example:_

```
|...|b|a| -> |...|b|
```

### Over

_Descirption:_ Copy the second element to the top

_Args:_ 2

_Tokens:_ over

_Example:_

```
|...|b|a| -> |...|b|a|b|
```

### Rot

_Descirption:_ Rotate the top 3 elements

_Args:_ 3

_Tokens:_ rot

_Example:_

```
|...|c|b|a| -> |...|b|a|c|
```

### Size

_Descirption:_ Push the size of the stack to itself

_Args:_ 0

_Tokens:_ size

_Example:_

```
|c|b|a| -> |c|b|a|3|
| |     -> |0|
```

---

## Math

### Square Root

_Descirption:_ Get the Square Root of the top element

_Args:_ 1

_Error:_ x can't be negative

_Tokens:_ √x, sqrt

_Example:_

```
|...|a| -> |...|√a|
```

### Factorial

_Descirption:_ Get the factorial of the top element

_Args:_ 1

_Tokens:_ x!, fact

_Example:_

```
|...|a| -> |...|a!|
```

### Exponential

_Descirption:_ Get the exponential of the top element

_Args:_ 1

_Tokens:_ exp

_Example:_

```
|...|a| -> |...|exp(a)|
```

### Natural Logarithm

_Descirption:_ Get the Natural Logarithm of the top element

_Args:_ 1

_Error:_ x can't be 0 or negative

_Tokens:_ log

_Example:_

```
|...|a| -> |...|log(a)|
```

### Sine

_Descirption:_ Get the Sine of the top element

_Args:_ 1

_Tokens:_ sin

_Example:_

```
|...|a| -> |...|sin(a)|
```

### Cosine

_Descirption:_ Get the Cosine of the top element

_Args:_ 1

_Tokens:_ cos

_Example:_

```
|...|a| -> |...|cos(a)|
```

### Tangent

_Descirption:_ Get the Tangent of the top element

_Args:_ 1

_Tokens:_ tan

_Example:_

```
|...|a| -> |...|tan(a)|
```

### Maximum

_Descirption:_ Get the Maximum of the top 2 elements

_Args:_ 2

_Tokens:_ ↑, max

_Example:_

```
|...|b|a| -> |...|max(a,b)|
```

### Minimum

_Descirption:_ Get the Minimum of the top 2 elements

_Args:_ 2

_Tokens:_ ↓, min

_Example:_

```
|...|b|a| -> |...|min(a,b)|
```

### Simetric

_Descirption:_ Get the Simetric of the top element

_Args:_ 1

_Tokens:_ -x, sim

_Example:_

```
|...|a| -> |...|-a|
```

### Floor

_Descirption:_ Get the largest integer before the top element

_Args:_ 1

_Tokens:_ ⌊x⌋, floor

_Example:_

```
|...|a| -> |...|⌊a⌋|
```

### Ceil

_Descirption:_ Get the smallest integer after the top element

_Args:_ 1

_Tokens:_ ⌈x⌉, ceil

_Example:_

```
|...|a| -> |...|⌈a⌉|
```

### Absolute Value

_Descirption:_ Get the Absolute Value of the top element

_Args:_ 1

_Tokens:_ |x|, abs

_Example:_

```
|...|a| -> |...| |a| |
```
