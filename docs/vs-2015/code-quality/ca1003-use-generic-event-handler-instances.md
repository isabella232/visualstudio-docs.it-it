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
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539906"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Usare istanze di gestori eventi generici
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft. Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contiene un delegato che restituisce void, la cui firma contiene due parametri (il primo oggetto e il secondo un tipo assegnabile a EventArgs) e le destinazioni dell'assembly contenitore [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Descrizione della regola
 Prima [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , per passare informazioni personalizzate al gestore eventi, era necessario dichiarare un nuovo delegato che specificava una classe derivata dalla <xref:System.EventArgs?displayProperty=fullName> classe. Questo non è più vero in [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , che ha introdotto il <xref:System.EventHandler%601?displayProperty=fullName> delegato. Questo delegato generico consente di usare tutte le classi derivate da <xref:System.EventArgs> in combinazione con il gestore eventi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il delegato e sostituirne l'utilizzo usando il <xref:System.EventHandler%601?displayProperty=fullName> delegato. Se il delegato viene generato automaticamente dal [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilatore, modificare la sintassi della dichiarazione di evento in modo da usare il <xref:System.EventHandler%601?displayProperty=fullName> delegato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un delegato che viola la regola. Nell' [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] esempio i commenti descrivono come modificare l'esempio per soddisfare la regola. Per l'esempio in C#, viene illustrato un esempio che mostra il codice modificato.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene rimossa la dichiarazione del delegato dall'esempio precedente, che soddisfa la regola e ne sostituisce l'uso nei `ClassThatRaisesEvent` `ClassThatHandlesEvent` metodi e usando il <xref:System.EventHandler%601?displayProperty=fullName> delegato.

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
