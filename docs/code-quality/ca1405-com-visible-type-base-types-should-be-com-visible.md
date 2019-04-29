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
ms.openlocfilehash: 65bddd599bb544e000ca1d1269b84e53f51843bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546072"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: I tipi di base del tipo visibile a COM devono essere visibili a COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Category|Microsoft.Interoperability|
|Modifica importante|DependsOnFix|

## <a name="cause"></a>Causa
 Un tipo visibile modello COM (Component Object) deriva da un tipo che non è visibile a COM.

## <a name="rule-description"></a>Descrizione della regola
 Quando un tipo visibile a COM consente di aggiungere membri in una nuova versione, deve attenersi alle indicazioni rigorose per evitare di interrompere l'associazione alla versione corrente dei client COM. Un tipo che non è visibile a COM si presuppone che non è necessario rispettare queste regole di controllo delle versioni di COM durante l'aggiunta di nuovi membri. Tuttavia, se un visibili a COM tipo deriva dal tipo visibile a COM ed espone un'interfaccia di classe <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (impostazione predefinita), tutti i membri pubblici del tipo di base (a meno che non siano specificamente contrassegnati come COM invisibili, che potrebbero essere ridondanti) sono esposte a COM. Se il tipo di base consente di aggiungere nuovi membri in una versione successiva, potrebbero interrompere qualsiasi client COM che sono associati all'interfaccia di classe del tipo derivato. Tipi visibili a COM devono derivare solo da tipi visibili a COM per ridurre il rischio di interrompere i client COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rendere invisibile il tipo derivato, COM o i tipi di base visibile a COM.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)