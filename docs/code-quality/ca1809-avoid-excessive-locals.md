---
title: "CA1809: Avoid excessive locals"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords:
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1809: Avoid excessive locals

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Category|Microsoft.Performance|
|Breaking Change|Non-breaking|

## Cause
A member contains more than 64 local variables, some of which might be compiler-generated.

## Rule description
A common performance optimization is to store a value in a processor register instead of in memory, which is referred to as *enregistering* the value. The common language runtime considers up to 64 local variables for enregistration. Variables that are not enregistered are put on the stack and must be moved to a register before manipulation. To allow the chance that all local variables get enregistered, limit the number of local variables to 64.

## How to fix violations
To fix a violation of this rule, refactor the implementation to use no more than 64 local variables.

## When to suppress warnings
It is safe to suppress a warning from this rule, or to disable the rule, if performance is not an issue.

## Related rules
[CA1804: Remove unused locals](../code-quality/ca1804-remove-unused-locals.md)