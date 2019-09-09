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
ms.openlocfilehash: a1ef4258d1b095395be34c7004e3f783b973897d
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547886"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Usare istanze di gestori eventi generici

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo contiene un delegato che restituisce void e la cui firma contiene due parametri (il primo oggetto e il secondo un tipo assegnabile a EventArgs) e l'assembly contenitore è destinato a .NET.

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Prima di .NET, per passare informazioni personalizzate al gestore eventi, era necessario dichiarare un nuovo delegato che specificava una classe derivata dalla <xref:System.EventArgs?displayProperty=fullName> classe. In .NET, il delegato <xref:System.EventHandler%601?displayProperty=fullName> generico consente di usare tutte le classi derivate da <xref:System.EventArgs> in combinazione con il gestore eventi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rimuovere il delegato e sostituirne l'utilizzo usando il <xref:System.EventHandler%601?displayProperty=fullName> delegato.

Se il delegato viene generato automaticamente dal compilatore Visual Basic, modificare la sintassi della dichiarazione di evento in modo da usare <xref:System.EventHandler%601?displayProperty=fullName> il delegato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un delegato che viola la regola. Nell'esempio Visual Basic, i commenti descrivono come modificare l'esempio per soddisfare la regola. Per l' C# esempio, di seguito viene illustrato un esempio di codice modificato.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

Il frammento di codice seguente rimuove la dichiarazione del delegato dall'esempio precedente, che soddisfa la regola. Sostituisce l'uso nei `ClassThatRaisesEvent` metodi e `ClassThatHandlesEvent` usando il <xref:System.EventHandler%601?displayProperty=fullName> delegato.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA1005 Evitare parametri eccessivi nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010 Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000 Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002 Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006 Non annidare tipi generici nelle firme membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004 I metodi generici devono fornire il parametro di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: Usare i generics laddove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Vedere anche

- [Generics](/dotnet/csharp/programming-guide/generics/index)