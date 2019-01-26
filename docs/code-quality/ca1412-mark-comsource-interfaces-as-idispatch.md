---
title: 'CA1412: Contrassegnare le interfacce ComSource come IDispatch'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 61a7042c4eae547a9da64503301351e96681f328
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013964"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Contrassegnare le interfacce ComSource come IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo è contrassegnato con il <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attributo e almeno un'interfaccia specificata non è contrassegnato con il <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attributo impostato sul `InterfaceIsDispatch` valore.

## <a name="rule-description"></a>Descrizione della regola

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> Consente di identificare le interfacce eventi che una classe espone ai client modello COM (Component Object). Queste interfacce devono essere esposti come `InterfaceIsIDispatch` per consentire ai client COM Visual Basic 6 ricevere le notifiche degli eventi. Per impostazione predefinita, se un'interfaccia non è contrassegnata con il <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attributo, viene esposta come un'interfaccia duale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere o modificare la <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> dell'attributo in modo che il relativo valore è impostato su InterfaceIsIDispatch per tutte le interfacce che vengono specificate con la <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attributo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata una classe in cui una delle interfacce viola la regola.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Regole correlate

[CA1408: Non utilizzare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche

- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)