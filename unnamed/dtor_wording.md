---
title: "Improved destructor call syntax"
document: PXXXX
date: 2019-11-20
audience: Evolution Working Group Incubator
author:
 - name: Krystian Stasiowski
   email: <sdkrystian@gmail.com>
toc: false
monofont: "DejaVu Sans Mono"
---

# Wording

Change definition of *unqualified-id* 

> *unqualified-id:* 

> > *identifier* \
> > *operator-function-id* \
> > *conversion-function-id* \
> > *literal-operator-id* \
> > *~type-name* \
> > *~decltype-specifier* \
> > *[~fundamental-type-specifier]{.add}* \
> > *template-id* \

Change definition of *qualified-id*

> *qualified-id:* 

> > *nested-name-specifier* `templateₒₚₜ` *unqualified-id* \
> > [*~nested-name-specifier* `templateₒₚₜ` *type-name*]{.add} \

Add new grammar term *fundamental-type-specifier* above *simple-type-specifier*

:::add
> *fundamental-type-specifier:*

> > `char` \
> > `char8_t` \
> > `char16_t` \
> > `char32_t` \
> > `wchar_t` \
> > `bool` \
> > `short` \
> > `int` \
> > `long` \
> > `signed` \
> > `unsigned` \
> > `float` \
> > `double` \
> > `void` \
:::

\pagebreak

Change definition of *simple-type-specifier*

> *simple-type-specifier:* 

> > *nested-name-specifier*`ₒₚₜ` *type-name* \
> > *nested-name-specifier* `template` *simple-template-id* \
> >	*decltype-specifier* \
> >	*placeholder-type-specifier* \
> > *nested-name-specifier*`ₒₚₜ` *template-name* \
> > [*fundamental-type-specifier*]{.add} \
> > [`char` \
> > `char8_t` \
> > `char16_t` \
> > `char32_t` \
> > `wchar_t` \
> > `bool` \
> > `short` \
> > `int` \
> > `long` \
> > `signed` \
> > `unsigned` \
> > `float` \
> > `double` \
> > `void`]{.rm}

Changes to [expr.prim.id.qual] p2

> [2]{.pnum} [[...] Where *type-name ​::​~ type-name* is used, the two *type-names* shall refer to the same type (ignoring cv-qualifications); this notation denotes the destructor of the type so named. [...]]{.rm}

Add a new paragraph below [expr.prim.id.qual] p2

:::add
> [3]{.pnum} For a *qualified-id* containing an *unqualified-id* of the form *~type-name* or *~fundamental-type-specifier*, the *nested-name-specifier* shall name the same type as the *type-name* or *fundamental-type-specifier*; the *qualified-id* denotes the destructor of the named type. A *qualified-id* of the form *~nested-name-specifier* `templateₒₚₜ` *type-name* denotes the destructor of the named type.
:::

Add a new paragraph below [basic.lookup.qual] p6

:::add
> [7]{.pnum} In a *qualified-id* of the form:

> > *~nested-name-specifier* `templateₒₚₜ` *type-name*

> The *type-name* is looked up in the scope of the *nested-name-specifier*.
:::

Changes to [basic.lookup.classref] p3

> [3]{.pnum} [...] [An *unqualified-id* of the form *~fundamental-type-specifier* is not looked up; it is assumed to name the pseudo-destructor of the named type.]{.add}

Add a new paragraph below [basic.lookup.classref] p5

:::add
> [6]{.pnum} If the *qualified-id* has the form:
	
> > *~nested-name-specifier* `templateₒₚₜ` *type-name*

> The *type-name* is looked up as specified in [basic.lookup.qual]; the lookup shall find a name that refers to the type of the object expression.
:::