---
title: 'CA1412: contrassegnare le interfacce ComSource come IDispatch | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652726"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Contrassegnare le interfacce ComSource come IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo è contrassegnato con l'attributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> e almeno un'interfaccia specificata non è contrassegnata con l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> impostato sul valore `InterfaceIsDispatch`.

## <a name="rule-description"></a>Descrizione della regola
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> viene usato per identificare le interfacce evento che una classe espone ai client Component Object Model (COM). Queste interfacce devono essere esposte come `InterfaceIsIDispatch` per consentire a Visual Basic 6 client COM di ricevere le notifiche degli eventi. Per impostazione predefinita, se un'interfaccia non è contrassegnata con l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, viene esposta come interfaccia duale.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, aggiungere o modificare l'attributo <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> in modo che il relativo valore sia impostato su InterfaceIsIDispatch per tutte le interfacce specificate con l'attributo <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una classe in cui una delle interfacce viola la regola.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Vedere anche
 [Procedura: generare eventi gestiti da un sink com](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [interoperabilità con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
