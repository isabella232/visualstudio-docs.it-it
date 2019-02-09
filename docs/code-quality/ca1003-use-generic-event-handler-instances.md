---
title: 'CA1003: Usare istanze di gestori eventi generici'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 89ee70694d81253c66fc83062c9736ba63f7e6e6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907308"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Usare istanze di gestori eventi generici

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo contiene un delegato che restituisce void, la cui firma contiene due parametri (il primo è un oggetto e il secondo è un tipo è assegnabile a EventArgs) la destinazione dell'assembly che lo contiene [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Descrizione della regola
 Prima di [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], per poter passare le informazioni personalizzate per il gestore eventi, un nuovo delegato doveva essere dichiarato che specifica una classe derivata dal <xref:System.EventArgs?displayProperty=fullName> classe. Ciò non è più true nella [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], ovvero introdotto il <xref:System.EventHandler%601?displayProperty=fullName> delegare. Consente a qualsiasi classe che deriva da questo delegato generico <xref:System.EventArgs> per essere usato con il gestore dell'evento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere il delegato e sostituire l'uso con il <xref:System.EventHandler%601?displayProperty=fullName> delegare. Se il delegato viene generata automaticamente per il [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilatore, modificare la sintassi della dichiarazione di evento da utilizzare il <xref:System.EventHandler%601?displayProperty=fullName> delegare.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un delegato che viola la regola. Nel [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] esempio, i commenti descrivono come modificare l'esempio per soddisfare la regola. Nell'esempio c#, vedere l'esempio seguente che mostra il codice modificato.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Esempio
 L'esempio seguente rimuove la dichiarazione di delegato dell'esempio precedente, che soddisfa la regola e sostituisce l'uso in di `ClassThatRaisesEvent` e `ClassThatHandlesEvent` metodi usando la <xref:System.EventHandler%601?displayProperty=fullName> delegare.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1005: Evitare un numero eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Le raccolte devono implementare l'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche

- [Generics](/dotnet/csharp/programming-guide/generics/index)