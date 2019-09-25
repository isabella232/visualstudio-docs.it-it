---
title: 'CA1044: Le proprietà non devono essere in sola scrittura'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0fb424627d88ede6c0677b8c45de4aab487ae498
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235812"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Le proprietà non devono essere in sola scrittura

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Una proprietà ha una funzione di accesso set ma non una funzione di accesso get.

Per impostazione predefinita, questa regola esamina solo i tipi pubblici, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Le funzioni di accesso get forniscono l'accesso in lettura a una proprietà e le funzioni di accesso di set forniscono l'accesso in scrittura. Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura. Questo perché consentire a un utente di impostare un valore e quindi impedire all'utente di visualizzare il valore non fornisce alcuna sicurezza. Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, aggiungere una funzione di accesso get alla proprietà. In alternativa, se è necessario il comportamento di una proprietà di sola scrittura, provare a convertire questa proprietà in un metodo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Si consiglia di non eliminare gli avvisi da questa regola.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1044.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio `BadClassWithWriteOnlyProperty` seguente è un tipo con una proprietà di sola scrittura. `GoodClassWithReadWriteProperty`contiene il codice corretto.

[!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
[!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]