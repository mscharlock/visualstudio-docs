---
title: "CA1005: Avoid excessive parameters on generic types"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords:
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1005: Avoid excessive parameters on generic types

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Category|Microsoft.Design|
|Breaking Change|Breaking|

## Cause
An externally visible generic type has more than two type parameters.

## Rule description
The more type parameters a generic type contains, the more difficult it is to know and remember what each type parameter represents. It is usually obvious with one type parameter, as in `List<T>`, and in certain cases with two type parameters, as in `Dictionary<TKey, TValue>`. If more than two type parameters exist, the difficulty becomes too great for most users (for example, `TooManyTypeParameters<T, K, V>` in C# or `TooManyTypeParameters(Of T, K, V)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## How to fix violations
To fix a violation of this rule, change the design to use no more than two type parameters.

## When to suppress warnings
Do not suppress a warning from this rule unless the design absolutely requires more than two type parameters. Providing generics in a syntax that is easy to understand and use reduces the time that is required to learn and increases the adoption rate of new libraries.

## Related rules
[CA1010: Collections should implement generic interface](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Do not declare static members on generic types](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Do not expose generic lists](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Do not nest generic types in member signatures](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Generic methods should provide type parameter](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Use generic event handler instances](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Use generics where appropriate](../code-quality/ca1007-use-generics-where-appropriate.md)

## See also
[Generics](/dotnet/csharp/programming-guide/generics/index)