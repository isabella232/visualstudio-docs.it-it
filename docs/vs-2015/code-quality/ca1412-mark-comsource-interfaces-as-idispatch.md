---
title: 'CA1412: Contrassegnare le interfacce ComSource come IDispatch | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c363f085a4db26b9383bd305ed01ec9cb8961a64
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274495"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Contrassegnare le interfacce ComSource come IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe in cui una delle interfacce viola la regola.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche
 [Procedura: generare eventi gestiti da un Sink COM](http://msdn.microsoft.com/en-us/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



