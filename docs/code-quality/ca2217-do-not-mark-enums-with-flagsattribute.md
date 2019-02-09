---
title: 'CA2217: Non contrassegnare le enumerazioni con FlagsAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce4036ef3c0c9ea177ea4225ed10ca7cfe128697
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926814"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Non contrassegnare le enumerazioni con FlagsAttribute

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un'enumerazione visibile esternamente è contrassegnata con <xref:System.FlagsAttribute>e ne ha uno o più valori che non sono potenze di due o una combinazione degli altri valori definiti nell'enumerazione.

## <a name="rule-description"></a>Descrizione della regola

Un'enumerazione deve avere <xref:System.FlagsAttribute> presente solo se ogni valore definiti nell'enumerazione è una potenza di due o una combinazione di valori definiti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere <xref:System.FlagsAttribute> ricavato dall'enumerazione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="example-that-should-not-have-the-attribute"></a>Esempio che non deve avere l'attributo

Nell'esempio seguente viene illustrata un'enumerazione, `Color`, che contiene il valore 3. 3 non è una potenza di due o una combinazione di uno qualsiasi dei valori definiti. Il `Color` enumerazione non deve essere contrassegnato con <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Esempio che deve avere l'attributo

L'esempio seguente mostra un'enumerazione `Days`, che soddisfa i requisiti per essere contrassegnata con <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.FlagsAttribute?displayProperty=fullName>
