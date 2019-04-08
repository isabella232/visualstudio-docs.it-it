---
title: "CA1036: Eseguire l'override di metodi su tipi confrontabili | Microsoft Docs"
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 127bb322a9dd5c841f71a5da49b0d9a6fceaf5e6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966916"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Eseguire l'override di metodi su tipi confrontabili
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo pubblico o protetto implementa il <xref:System.IComparable?displayProperty=fullName> l'interfaccia e non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName> o non esegue l'overload di operatore specifico del linguaggio per uguaglianza, ineguaglianza, minore o maggiore di. La regola non indica una violazione se il tipo eredita solo un'implementazione dell'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 I tipi che definiscono un ordinamento personalizzato implementano il <xref:System.IComparable> interfaccia. Il <xref:System.IComparable.CompareTo%2A> metodo restituisce un valore intero che indica l'ordinamento corretto delle due istanze del tipo. Questa regola identifica i tipi che impostare un ordine decrescente. Ciò implica che il significato normale di uguaglianza, ineguaglianza, minore di, maggiore e non si applicano. Quando si fornisce un'implementazione di <xref:System.IComparable>, è necessario in genere anche eseguire l'override <xref:System.Object.Equals%2A> in modo che restituisca i valori che siano coerenti con <xref:System.IComparable.CompareTo%2A>. Se esegue l'override <xref:System.Object.Equals%2A> e scrive il codice in un linguaggio che supporta l'overload dell'operatore, è inoltre necessario fornire gli operatori che siano coerenti con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, eseguire l'override <xref:System.Object.Equals%2A>. Se il linguaggio di programmazione supporta l'overload degli operatori, specificare gli operatori seguenti:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  In C#, i token che vengono usati per rappresentare questi operatori sono i seguenti: = =,! =, \<, e >.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se la violazione è causata da operatori mancanti e il linguaggio di programmazione non supporta l'overload degli operatori, come avviene con Visual Basic .NET. È anche possibile eliminare un avviso per da questa regola quando viene attivato per gli operatori di uguaglianza diverso da op_Equality se si determina che implementa gli operatori non ha senso nel contesto dell'applicazione. Tuttavia, dovrebbe essere sempre op_Equality e l'operatore = =, se si esegue l'override di Object. Equals.

## <a name="example"></a>Esempio
 L'esempio seguente contiene un tipo che implementa correttamente <xref:System.IComparable>. Commenti del codice identificano i metodi che soddisfano diverse regole che riguardano <xref:System.Object.Equals%2A> e il <xref:System.IComparable> interfaccia.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione seguente testa il comportamento del <xref:System.IComparable> implementazione descritto in precedenza.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operatori di uguaglianza](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
