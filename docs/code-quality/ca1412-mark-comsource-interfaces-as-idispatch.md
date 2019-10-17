---
title: 'CA1412: Contrassegnare le interfacce ComSource come IDispatch'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 227cc5c47a2001cd6c3b71718ae2a29032bed71c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444206"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Contrassegnare le interfacce ComSource come IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Category|Microsoft. interoperabilità|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo è contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> e almeno un'interfaccia specificata non è contrassegnata con l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> impostato sul valore `InterfaceIsDispatch`.

## <a name="rule-description"></a>Descrizione della regola

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> viene usato per identificare le interfacce evento che una classe espone ai client Component Object Model (COM). Queste interfacce devono essere esposte come `InterfaceIsIDispatch` per consentire a Visual Basic 6 client COM di ricevere le notifiche degli eventi. Per impostazione predefinita, se un'interfaccia non è contrassegnata con l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, viene esposta come interfaccia duale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere o modificare l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> in modo che il relativo valore sia impostato su InterfaceIsIDispatch per tutte le interfacce specificate con l'attributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata una classe in cui una delle interfacce viola la regola.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche

- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
