---
title: 'CA1003: Usare istanze di gestori eventi generici | Microsoft Docs'
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
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3c2cf2ad59f7ade337c84f13133bb5181afb615
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929088"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>Ca1003: Utilizzare istanze di gestori eventi generici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contiene un delegato che restituisce void, la cui firma contiene due parametri (il primo è un oggetto e il secondo è un tipo è assegnabile a EventArgs) la destinazione dell'assembly che lo contiene [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Descrizione della regola
 Prima di [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], per poter passare le informazioni personalizzate per il gestore eventi, un nuovo delegato doveva essere dichiarato che specifica una classe derivata dal <xref:System.EventArgs?displayProperty=fullName> classe. Ciò non è più true nella [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], ovvero introdotto il <xref:System.EventHandler%601?displayProperty=fullName> delegare. Consente a qualsiasi classe che deriva da questo delegato generico <xref:System.EventArgs> per essere usato con il gestore dell'evento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il delegato e sostituire l'uso con il <xref:System.EventHandler%601?displayProperty=fullName> delegare. Se il delegato viene generata automaticamente per il [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilatore, modificare la sintassi della dichiarazione di evento da utilizzare il <xref:System.EventHandler%601?displayProperty=fullName> delegare.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un delegato che viola la regola. Nel [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] esempio, i commenti descrivono come modificare l'esempio per soddisfare la regola. Nell'esempio c#, vedere l'esempio seguente che mostra il codice modificato.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Esempio
 L'esempio seguente rimuove la dichiarazione di delegato dell'esempio precedente, che soddisfa la regola e sostituisce l'uso in di `ClassThatRaisesEvent` e `ClassThatHandlesEvent` metodi usando la <xref:System.EventHandler%601?displayProperty=fullName> delegare.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono specificare parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Usare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche
 [Generics](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



