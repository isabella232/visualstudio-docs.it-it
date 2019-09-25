---
title: 'CA1721: I nomi delle proprietà non devono corrispondere ai metodi get'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 805ceb7abf7096df29894a23be6c8e7b1f6bd5b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233912"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: I nomi delle proprietà non devono corrispondere ai metodi get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|Category|Microsoft.Naming|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Il nome di un membro inizia con "Get" e in caso contrario corrisponde al nome di una proprietà. Ad esempio, un tipo che contiene un metodo denominato ' GetColor ' e una proprietà denominata ' color ' causano una violazione della regola.

Per impostazione predefinita, questa regola esamina solo le proprietà e i membri visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

I metodi "Get" e le proprietà devono avere nomi indicano chiaramente la distinzione tra le funzioni.

Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. Questa coerenza riduce il tempo necessario per apprendere una nuova libreria software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Modificare il nome in modo che non corrisponda al nome di un metodo con prefisso "Get".

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

> [!NOTE]
> Questo avviso può essere escluso se il metodo "Get" è causato dall'implementazione dell'interfaccia IExtenderProvider.

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1721.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

L'esempio seguente contiene un metodo e una proprietà che violano questa regola.

[!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
[!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Regole correlate

- [CA1024: Usare le proprietà laddove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)