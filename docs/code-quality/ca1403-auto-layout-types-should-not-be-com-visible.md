---
title: 'CA1403: I tipi layout automatici non devono essere visibili a COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234828"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: I tipi layout automatici non devono essere visibili a COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft. interoperabilità|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo di valore visibile Component Object Model (com) è contrassegnato con <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> l'attributo impostato <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>su.

## <a name="rule-description"></a>Descrizione della regola

<xref:System.Runtime.InteropServices.LayoutKind>i tipi di layout vengono gestiti dal Common Language Runtime. Il layout di questi tipi può variare tra le versioni di .NET, che interrompe i client COM che prevedono un layout specifico. Se l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attributo non è specificato, i C#compilatori, C++ Visual Basic e specificano [LayoutKind. auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) per i tipi di valore.

A meno che non sia contrassegnato diversamente, tutti i tipi pubblici, non generici sono visibili a COM e tutti i tipi non pubblici e generici sono invisibili a COM. Tuttavia, per ridurre i falsi positivi, questa regola richiede che la visibilità COM del tipo venga dichiarata in modo esplicito. L'assembly contenitore deve <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> essere contrassegnato con impostato su `false` e il tipo <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve essere contrassegnato con impostato su `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il valore dell' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attributo in [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) o [LayoutKind. Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)oppure rendere il tipo invisibile a com.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che soddisfa la regola.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche

- [Qualifica tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)