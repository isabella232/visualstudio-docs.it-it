---
title: "CA1036: eseguire l'override di metodi su tipi confrontabili | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52247c9175b22d3d96aa91557ee133f37c55e789
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546601"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Eseguire l'override di metodi su tipi confrontabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft. Design|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto implementa l' <xref:System.IComparable?displayProperty=fullName> interfaccia e non esegue l'override di o non esegue <xref:System.Object.Equals%2A?displayProperty=fullName> l'overload dell'operatore specifico della lingua per verificarne l'uguaglianza, la disuguaglianza, minore di o maggiore di. La regola non segnala una violazione se il tipo eredita solo un'implementazione dell'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 I tipi che definiscono un ordinamento personalizzato implementano l' <xref:System.IComparable> interfaccia. Il <xref:System.IComparable.CompareTo%2A> metodo restituisce un valore intero che indica l'ordinamento corretto per due istanze del tipo. Questa regola identifica i tipi che impostano un ordinamento. Ciò implica che il significato comune di uguaglianza, disuguaglianza, minore di e maggiore di non si applicano. Quando si fornisce un'implementazione di <xref:System.IComparable> , è necessario in genere eseguire l'override di <xref:System.Object.Equals%2A> in modo che restituisca valori coerenti con <xref:System.IComparable.CompareTo%2A> . Se si esegue l'override di <xref:System.Object.Equals%2A> e si codifica in un linguaggio che supporta gli overload degli operatori, è necessario fornire anche operatori coerenti con <xref:System.Object.Equals%2A> .

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, eseguire l'override di <xref:System.Object.Equals%2A> . Se il linguaggio di programmazione supporta l'overload degli operatori, fornire gli operatori seguenti:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  In C#, i token usati per rappresentare questi operatori sono i seguenti: = =,! =, \<, and > .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola quando la violazione è causata da operatori mancanti e il linguaggio di programmazione in uso non supporta l'overload degli operatori, come nel caso di Visual Basic .NET. È anche possibile eliminare un avviso per da questa regola quando viene attivato su operatori di uguaglianza diversi da op_Equality se si determina che l'implementazione degli operatori non è sensata nel contesto dell'applicazione. Tuttavia, se si esegue l'override di Object. Equals, è sempre necessario op_Equality e l'operatore = =.

## <a name="example"></a>Esempio
 Nell'esempio seguente è contenuto un tipo che implementa correttamente <xref:System.IComparable> . I commenti del codice identificano i metodi che soddisfano varie regole correlate a <xref:System.Object.Equals%2A> e all' <xref:System.IComparable> interfaccia.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Esempio
 Nell'applicazione seguente viene testato il comportamento dell' <xref:System.IComparable> implementazione mostrata in precedenza.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operatori di uguaglianza](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
