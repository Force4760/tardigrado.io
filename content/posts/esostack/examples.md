+++
title = "Examples"
date = "2022-02-19"
tags = ['EsoStack', 'Coding', 'Docs', 'EsoLangs']
description = " "
+++

---

## AllEqual

_Description:_ Check if all elements are equal

_Code:_

```
(get the maximum of the stack)
duplicate 2 2 size / -
for { max }

(get the minimum of the stack)
duplicate 2 2 size / -
for { min }

(compare them)
==
```

## Factorial

_Description:_ Get the factorial of N

_Code:_

```
(generate a list like: 1 2 ... N N)
N 0 swap for {
    1 + dup
}

(turn the stack into: ... 1 2 ... N [N-1])
1 swap -

(multiply to get the factorial)
for { * }

```

---
