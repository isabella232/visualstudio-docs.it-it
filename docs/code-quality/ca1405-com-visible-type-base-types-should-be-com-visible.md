---
title: 'CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e4e5c4ed258bcc88fedbb6d015fed576d326a0f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234963"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft. interoperabilità|
|Modifica|DependsOnFix|

## <a name="cause"></a>Causa
Un tipo visibile di Component Object Model (COM) deriva da un tipo non visibile a COM.

## <a name="rule-description"></a>Descrizione della regola
Quando un tipo visibile a COM aggiunge membri in una nuova versione, deve attenersi alle linee guida rigorose per evitare di suddividere i client COM che si associano alla versione corrente. Un tipo invisibile a COM presume che non debba seguire queste regole di controllo delle versioni COM quando aggiunge nuovi membri. Tuttavia, se un tipo visibile a com deriva dal tipo com invisibile ed espone un'interfaccia di classe di <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (impostazione predefinita), tutti i membri pubblici del tipo di base (a meno che non siano contrassegnati in modo esplicito come com invisibile, che sarebbe ridondante) sono esposti a COM. Se il tipo di base aggiunge nuovi membri in una versione successiva, eventuali client COM che si associano all'interfaccia della classe del tipo derivato potrebbero interrompersi. I tipi visibili a COM dovrebbero derivare solo da tipi visibili a COM per ridurre la possibilità di suddividere i client COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rendere visibili i tipi di base o il tipo derivato COM invisibile.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un tipo che viola la regola.

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)