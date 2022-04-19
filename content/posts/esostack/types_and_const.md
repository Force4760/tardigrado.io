+++
title = "Types"
date = "2022-02-19"
tags = ['EsoStack', 'Coding', 'Docs', 'EsoLangs']
description = " "
+++

---

## Number

EsoStack only knows one type: **Number**

A stack can hold as many **Numbers** as you want (i.e. as your Computer allows)

This **Numbers** can be added to the stack by simply typing them. They are represented only with 2 decimal places, but internally they are stored with higher precision.

_Examples:_

```
-> 42 420 100
   | 42.00 | 420.00 | 100.00 |

-> 4.2 42.0 123.123
   | 4.20 | 42.00 | 123.12 |
```

---

## Boolean

In EsoStack even **Booleans** are **Numbers**.

**true** corresponds to **1**

**false** corresponds to **0**

_Examples:_

```
-> true 5 &&
   | 1.00 | 5.00 | -> | 1.00 |

-> false 0 ==
   | 0.00 | 0.00 | -> | 1.00 |

-> true 3 +
   | 1.00 | 3.00 | -> | 4.00 |
```

---

## Constants

EsoStack provides some constants to help with calculations.

### Pi

_Tokens:_ π, pi

_Value:_ 3.1415926536

### Tau

_Tokens:_ τ, 2π, tau

_Value:_ 6.2831853072

### Phi

_Tokens:_ ϕ, phi

_Value:_ 1.6180339887

### Euler's Number

_Tokens:_ e

_Value:_ 2.7182818285
