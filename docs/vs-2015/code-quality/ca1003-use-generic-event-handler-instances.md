---
title: 'Ca1003: usare istanze di gestori eventi generici | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34318d3fb01f3f8dee50da2bc534908cecbdaf32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646294"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>Ca1003: Utilizzare istanze di gestori eventi generici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contiene un delegato che restituisce void, la cui firma contiene due parametri (il primo oggetto e il secondo un tipo assegnabile a EventArgs) e l'assembly contenitore ha come destinazione [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Descrizione della regola
 Prima di [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], per passare informazioni personalizzate al gestore eventi, era necessario dichiarare un nuovo delegato che specificava una classe derivata dalla classe <xref:System.EventArgs?displayProperty=fullName>. Questo non è più vero in [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], che ha introdotto il delegato di <xref:System.EventHandler%601?displayProperty=fullName>. Questo delegato generico consente di usare tutte le classi derivate da <xref:System.EventArgs> insieme al gestore dell'evento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il delegato e sostituirne l'utilizzo usando il delegato <xref:System.EventHandler%601?displayProperty=fullName>. Se il delegato viene generato automaticamente dal compilatore [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], modificare la sintassi della dichiarazione di evento in modo da usare il delegato di <xref:System.EventHandler%601?displayProperty=fullName>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un delegato che viola la regola. Nell'esempio [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], i commenti descrivono come modificare l'esempio per soddisfare la regola. Per l' C# esempio, di seguito viene illustrato un esempio di codice modificato.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene rimossa la dichiarazione del delegato dall'esempio precedente, che soddisfa la regola e ne sostituisce l'uso nei metodi `ClassThatRaisesEvent` e `ClassThatHandlesEvent` utilizzando il delegato <xref:System.EventHandler%601?displayProperty=fullName>.

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
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
