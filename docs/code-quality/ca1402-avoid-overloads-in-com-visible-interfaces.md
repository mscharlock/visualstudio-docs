---
title: "CA1402: Avoid overloads in COM visible interfaces"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords:
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1402: Avoid overloads in COM visible interfaces

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Category|Microsoft.Interoperability|
|Breaking Change|Breaking|

## Cause
A Component Object Model (COM) visible interface declares overloaded methods.

## Rule description
When overloaded methods are exposed to COM clients, only the first method overload retains its name. Subsequent overloads are uniquely renamed by appending to the name an underscore character '_' and an integer that corresponds to the order of declaration of the overload. For example, consider the following methods:

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

These methods are exposed to COM clients as the following.

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Visual Basic 6 COM clients cannot implement interface methods by using an underscore in the name.

## How to fix violations
To fix a violation of this rule, rename the overloaded methods so that the names are unique. Alternatively, make the interface invisible to COM by changing the accessibility to `internal` (`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) or by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> attribute set to `false`.

## When to suppress warnings
Do not suppress a warning from this rule.

## Example
The following example shows an interface that violates the rule and an interface that satisfies the rule.

[!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
[!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## Related rules
[CA1413: Avoid non-public fields in COM visible value types](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Avoid static members in COM visible types](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Mark assemblies with ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## See also

- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index)
- [Long Data Type](/dotnet/visual-basic/language-reference/data-types/long-data-type)