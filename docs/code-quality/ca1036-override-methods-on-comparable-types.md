---
title: "CA1036: Eseguire l'override di metodi su tipi confrontabili"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed69ba759d63ba27114bc097ac1fd9ccbe424edd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547738"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Eseguire l'override di metodi su tipi confrontabili

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto implementa il <xref:System.IComparable?displayProperty=fullName> l'interfaccia e non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName> o non esegue l'overload dell'operatore di linguaggio specifico per verificarne l'uguaglianza, disuguaglianza, meno-rispetto a, o versione successiva-rispetto a. La regola non indica una violazione se il tipo eredita solo un'implementazione dell'interfaccia.

## <a name="rule-description"></a>Descrizione della regola

I tipi che definiscono un ordinamento personalizzato implementano il <xref:System.IComparable> interfaccia. Il <xref:System.IComparable.CompareTo%2A> metodo restituisce un valore intero che indica l'ordinamento corretto delle due istanze del tipo. Questa regola identifica i tipi che impostare un criterio di ordinamento. L'impostazione di una sequenza di ordinamento implica che il significato normale di uguaglianza, disuguaglianza, less-e maggiori-rispetto a non sono applicabili. Quando si fornisce un'implementazione di <xref:System.IComparable>, è necessario in genere anche eseguire l'override <xref:System.Object.Equals%2A> in modo che restituisca i valori che siano coerenti con <xref:System.IComparable.CompareTo%2A>. Se esegue l'override <xref:System.Object.Equals%2A> e scrive il codice in un linguaggio che supporta l'overload dell'operatore, è inoltre necessario fornire gli operatori che siano coerenti con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, eseguire l'override <xref:System.Object.Equals%2A>. Se il linguaggio di programmazione supporta l'overload degli operatori, specificare gli operatori seguenti:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

In c#, i token che vengono usati per rappresentare questi operatori sono i seguenti:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da regola CA1036 quando la violazione è causata dalla mancanza di operatori e il linguaggio di programmazione non supporta l'overload degli operatori, come avviene con Visual Basic. È anche possibile eliminare un avviso per da questa regola quando viene attivato per gli operatori di uguaglianza diverso da op_Equality se si determina che implementa gli operatori non ha senso nel contesto dell'applicazione. Tuttavia, dovrebbe essere sempre op_Equality e l'operatore = =, se si esegue l'override di Object. Equals.

## <a name="example"></a>Esempio
 L'esempio seguente contiene un tipo che implementa correttamente <xref:System.IComparable>. Commenti del codice identificano i metodi che soddisfano diverse regole che riguardano <xref:System.Object.Equals%2A> e il <xref:System.IComparable> interfaccia.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Esempio
 L'applicazione seguente testa il comportamento del <xref:System.IComparable> implementazione descritto in precedenza.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)