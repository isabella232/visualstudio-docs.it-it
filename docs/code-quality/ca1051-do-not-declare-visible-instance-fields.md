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
ms.openlocfilehash: 69fb85c396da1acde40cd9bc46150ca5f1386c17
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449136"
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: Non dichiarare campi di istanza visibili

|||
|-|-|
|TypeName|DoNotDeclareVisibleInstanceFields|
|CheckId|CA1051|
|Category|Microsoft. Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa

Un tipo dispone di un campo di istanza non privata.

Per impostazione predefinita, questa regola esamina solo i tipi visibili esternamente, ma è [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

L'utilizzo principale di un campo deve essere come dettaglio di implementazione. I campi devono essere `private` o `internal` e devono essere esposti usando le proprietà. Per accedere a una proprietà è facile accedere a un campo e il codice nelle funzioni di accesso di una proprietà può cambiare quando le funzionalità del tipo vengono espanse senza introdurre modifiche di rilievo.

Le proprietà che restituiscono il valore di un campo privato o interno sono ottimizzate per essere eseguite in modo analogo all'accesso a un campo. il miglioramento delle prestazioni derivante dall'utilizzo di campi visibili esternamente anziché di proprietà è minimo. *Visibile esternamente* si riferisce ai livelli di accessibilità `public`, `protected` e `protected internal` (`Public`, `Protected` e `Protected Friend` in Visual Basic).

Inoltre, i campi pubblici non possono essere protetti tramite [richieste di collegamento](/dotnet/framework/misc/link-demands). Per altre informazioni, vedere [CA2112: i tipi protetti non devono esporre i campi](../code-quality/ca2112.md). (Le richieste di collegamento non sono applicabili alle app .NET Core).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, rendere il campo `private` o `internal` ed esporlo usando una proprietà visibile esternamente.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non visualizzare più questo avviso se si è certi che gli utenti debbano accedere direttamente al campo. Per la maggior parte delle applicazioni, i campi esposti non forniscono vantaggi a livello di prestazioni o di gestibilità rispetto alle proprietà.

I consumer possono richiedere l'accesso ai campi nelle situazioni seguenti:

- in controlli contenuto Web Form ASP.NET
- Quando la piattaforma di destinazione USA `ref` per modificare i campi, ad esempio i framework MVC (Model-View-ViewModel) per WPF e UWP

## <a name="configurability"></a>Configurabilità

Se questa regola viene eseguita da [analizzatori FxCop](install-fxcop-analyzers.md) (e non con analisi legacy), è possibile configurare le parti della codebase su cui eseguire questa regola, in base all'accessibilità. Ad esempio, per specificare che la regola deve essere eseguita solo sulla superficie dell'API non pubblica, aggiungere la coppia chiave-valore seguente a un file con estensione EditorConfig nel progetto:

```ini
dotnet_code_quality.ca1051.api_surface = private, internal
```

È possibile configurare questa opzione solo per questa regola, per tutte le regole o per tutte le regole in questa categoria (progettazione). Per altre informazioni, vedere [configurare gli analizzatori FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un tipo (`BadPublicInstanceFields`) che viola questa regola. `GoodPublicInstanceFields` Visualizza il codice corretto.

[!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]

## <a name="related-rules"></a>Regole correlate

- [CA2112: I tipi protetti non devono esporre campi](../code-quality/ca2112.md)

## <a name="see-also"></a>Vedere anche

- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
