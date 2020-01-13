---
title: "Down with array parameters! (for now)"	
document: DXXXXRX	
date: 2020-01-13	
audience: Evolution Working Group	
author:	
 - name: Krystian Stasiowski	
   email: <sdkrystian@gmail.com>	
 - name: Theodoric Stier	
   email: <kerdek7@gmail.com>	
toc: false
---

# Abstract

Deprecate parameters of array type to allow better use in future standardization.

# Wording

Add a note to [dcl.fct] p5

> [5]{.pnum} After determining the type of each parameter, any parameter of type “array of `T`” or of function type `T` is adjusted to be “pointer to `T`”. [\[ *Note:* Declaring a function parameter to have array type is deprecated. — *end note* \]]{.add}

Add a note to [temp.param] p10

> [10]{.pnum} A non-type *template-parameter* of type “array of `T`” or of function type `T` is adjusted to be of type “pointer to `T`”. [\[ *Note:* Declaring a non-type template parameter to have array type is deprecated. — *end note* \]]{.add}

Add a note to [except.handle] p2

> [2]{.pnum} A handler of type “array of `T`” or function type `T` is adjusted to be of type “pointer to `T`”. [\[ *Note:* Declaring a handler to have array type is deprecated. — *end note* \]]{.add}

Add a new subclause [depr.array.param] to [depr]

:::add
**D.5 Parameters of array type [depr.array.param]**

> [1]{.pnum} Declaring a function parameter, handler, or non-type template parameter to have array type is deprecated. \newline \[ *Note:* The types of such declarations is adjusted from "array of `T`" to "pointer to `T`". — *end note* \] \[ *Example:*
	```cpp
	template<const int a[]> // deprecated
	void f(const int c[4]) // deprecated
	{
​		try { throw a; }
​		catch (int c[]) { } // deprecated
	}
	```
— *end example* \]
:::