---
title: 'CA1003: Usare istanze di gestori eventi generici'
ms.date: 03/11/2019
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
ms.openlocfilehash: 66bb2b2229608c1a7710b7c5c71cbc0d701234e3
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714384"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Usare istanze di gestori eventi generici

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo contiene un delegato che restituisce void e la cui firma contiene due parametri (il primo è un oggetto e il secondo è un tipo è assegnabile a EventArgs) e le destinazioni .NET assembly che lo contiene.

Per impostazione predefinita, questa regola cerca solo tipi visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Prima di .NET, per passare le informazioni personalizzate per il gestore eventi, un nuovo delegato doveva essere dichiarato che specifica una classe derivata dal <xref:System.EventArgs?displayProperty=fullName> classe. In .NET, il tipo generico <xref:System.EventHandler%601?displayProperty=fullName> delegato consente a qualsiasi classe che deriva da <xref:System.EventArgs> per essere usato con il gestore dell'evento.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il delegato e sostituire l'uso con il <xref:System.EventHandler%601?displayProperty=fullName> delegare.

Se il delegato viene generata automaticamente dal compilatore Visual Basic, modificare la sintassi della dichiarazione evento per usare il <xref:System.EventHandler%601?displayProperty=fullName> delegare.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

L'esempio seguente illustra un delegato che viola la regola. Nell'esempio Visual Basic, i commenti descrivono come modificare l'esempio per soddisfare la regola. Nell'esempio c#, vedere l'esempio seguente che mostra il codice modificato.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Il frammento di codice seguente rimuove la dichiarazione di delegato dell'esempio precedente, che soddisfa la regola. Sostituisce l'uso in di `ClassThatRaisesEvent` e `ClassThatHandlesEvent` metodi usando la <xref:System.EventHandler%601?displayProperty=fullName> delegare.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1005: Evitare un numero eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: Le raccolte devono implementare l'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche

- [Generics](/dotnet/csharp/programming-guide/generics/index)