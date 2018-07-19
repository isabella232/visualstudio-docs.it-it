---
title: 'CA1403: I tipi layout automatici non devono essere visibili a COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d84fdd4f352a823614832cc8d5d1b9e57c7a9dfb
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058074"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: I tipi layout automatici non devono essere visibili a COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo di valore visibile modello COM (Component Object) è contrassegnato con il <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attributo è impostato su <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Descrizione della regola

<xref:System.Runtime.InteropServices.LayoutKind> tipi di layout sono gestiti da common language runtime. Il layout di questi tipi può variare tra le versioni di .NET Framework, che interrompe i client COM che prevedono un layout specifico. Se il <xref:System.Runtime.InteropServices.StructLayoutAttribute> attributo viene omesso, i compilatori c#, Visual Basic e C++ specificano [LayoutKind](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) per i tipi di valore.

Se non diversamente specificato, tutti i tipi pubblici e non generica sono visibili a COM, e tutti i tipi generici e non pubblici non sono visibili a COM. Tuttavia, per ridurre i falsi positivi, questa regola richiede la visibilità COM per essere dichiarata in modo esplicito il tipo. L'assembly che contiene deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostata su `false` e il tipo deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true`.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, modificare il valore della <xref:System.Runtime.InteropServices.StructLayoutAttribute> dell'attributo [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) o [LayoutKind](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), oppure rendere il tipo visibile a COM.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che soddisfa la regola.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche

- [Qualificare i tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)