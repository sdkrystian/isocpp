---
title: "Portable constexpr pointer comparisons"	
document: DXXXXRX	
date: 2020-02-05
audience: Library Evolution Working Group Incubator	
author:	
 - name: Krystian Stasiowski	
   email: <sdkrystian@gmail.com>	
toc: false
---

# Abstract

Introduce `ptr_in_range`, a function that checks if a pointer lies within a range with well defined results, and thereby allowing its use in constant expressions.

# Wording

Add a subclause [specialized.in.range] to [specialized.algorithms] 

The range checked for the pointer value must be valid, as the intent is to allow for a implementation to iterate over the range, and use the built-in equality operator to compare the pointer values (at least during constant evaluation). Pointer values can only exist for certain addresses corresponding to the alignmentment requirements of the pointed to type, so the results of passing such a pointer to the function is unspecified. \

:::add
**20.10.11.3 \ \ \ \ `ptr_in_range`**\

```cpp
template<typename T>
constexpr bool ptr_in_range(const T* first, const T* last, const T* ptr) noexcept;
```
 \

> [1]{.pnum} *Mandates:* `const T*` is an object pointer type.

> [2]{.pnum} *Preconditions:* `last` shall be reachable from `first`.

> [3]{.pnum} *Returns:* If the address *A* represented by `ptr` does not satisfy the alignment requirements of `T`, the result is unspecified. Otherwise, the result is `true` if there exists a pointer value of type *cv* `T` that represents the same address as `ptr` in the range `[first, last)`, and `false` otherwise.
:::
