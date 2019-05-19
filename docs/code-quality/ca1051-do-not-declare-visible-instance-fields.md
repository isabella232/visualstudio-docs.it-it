---
title: 'CA1051: Non dichiarare campi di istanza visibili'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c77678b1f09b1cf51a63f260252ddeaf9321fd5
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842075"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Non dichiarare campi di istanza visibili

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un tipo ha un campo di istanza pubblici.

Per impostazione predefinita, questa regola cerca solo tipi visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

L'utilizzo principale di un campo deve essere come dettaglio di implementazione. I campi devono essere `private` o `internal` e devono essere esposti tramite proprietà. È sufficiente accedere a una proprietà è di accedere a un campo e può modificare il codice in funzioni di accesso di una proprietà come espandono le funzionalità del tipo senza introdurre modifiche di rilievo. Le proprietà che restituiscono il valore di un campo privato o interno sono ottimizzate per l'esecuzione coerente con l'accesso a un campo. molto piccolo miglioramento delle prestazioni è associato l'utilizzo di campi visibili esternamente rispetto alle proprietà.

Visibile esternamente si intende `public`, `protected`, e `protected internal` (`Public`, `Protected`, e `Protected Friend` in Visual Basic) dei livelli di accessibilità.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, impostare il campo `private` o `internal` ed esporlo tramite una proprietà visibile esternamente.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola. Campi visibili esternamente non offre vantaggi che non sono disponibili per le proprietà. Inoltre, i campi pubblici non possono essere protetti da [richieste di collegamento](/dotnet/framework/misc/link-demands). Vedere [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo (`BadPublicInstanceFields`) che violano questa regola. `GoodPublicInstanceFields` Mostra il codice corretto.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

## <a name="see-also"></a>Vedere anche

- [Richieste di collegamento](/dotnet/framework/misc/link-demands)