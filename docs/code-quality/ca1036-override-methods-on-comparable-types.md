---
title: "CA1036: Eseguire l'override di metodi su tipi confrontabili"
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12b00c202373310b04021a46e74af2af7e10d535
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868873"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Eseguire l'override di metodi su tipi confrontabili

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un tipo implementa la <xref:System.IComparable?displayProperty=fullName> l'interfaccia e non esegue l'override <xref:System.Object.Equals%2A?displayProperty=fullName> o non esegue l'overload dell'operatore di linguaggio specifico per verificarne l'uguaglianza, disuguaglianza, meno-, maggiore o -rispetto. La regola non indica una violazione se il tipo eredita solo un'implementazione dell'interfaccia.

Per impostazione predefinita, questa regola considerati solo i tipi pubblici e protetti, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

I tipi che definiscono un ordinamento personalizzato implementano il <xref:System.IComparable> interfaccia. Il <xref:System.IComparable.CompareTo%2A> metodo restituisce un valore intero che indica l'ordinamento corretto delle due istanze del tipo. Questa regola identifica i tipi che impostare un criterio di ordinamento. L'impostazione di una sequenza di ordinamento implica che il significato normale di uguaglianza, disuguaglianza, less-e maggiori-rispetto a non sono applicabili. Quando si fornisce un'implementazione di <xref:System.IComparable>, è necessario in genere anche eseguire l'override <xref:System.Object.Equals%2A> in modo che restituisca i valori che siano coerenti con <xref:System.IComparable.CompareTo%2A>. Se esegue l'override <xref:System.Object.Equals%2A> e scrive il codice in un linguaggio che supporta l'overload dell'operatore, è inoltre necessario fornire gli operatori che siano coerenti con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, eseguire l'override <xref:System.Object.Equals%2A>. Se il linguaggio di programmazione supporta l'overload degli operatori, specificare gli operatori seguenti:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

In C#, i token che vengono usati per rappresentare questi operatori sono i seguenti:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da regola CA1036 quando la violazione è causata dalla mancanza di operatori e il linguaggio di programmazione non supporta l'overload degli operatori, come avviene con Visual Basic. Se si determina che implementa gli operatori non ha senso nel contesto dell'app, è anche possibile eliminare un avviso da questa regola quando viene attivato per gli operatori di uguaglianza diverso da op_Equality. Tuttavia, si deve sempre eseguire l'override op_Equality e l'operatore = =, se esegue l'override <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1036.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="examples"></a>Esempi

Il codice seguente contiene un tipo che implementa correttamente <xref:System.IComparable>. Commenti del codice identificano i metodi che soddisfano diverse regole che riguardano <xref:System.Object.Equals%2A> e il <xref:System.IComparable> interfaccia.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Il codice dell'applicazione seguente testa il comportamento del <xref:System.IComparable> implementazione descritto in precedenza.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Vedere anche

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatori di uguaglianza](/dotnet/standard/design-guidelines/equality-operators)