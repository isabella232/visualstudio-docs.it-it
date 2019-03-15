---
title: 'CA1305: Specificare IFormatProvider'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: b96ca08b51bb5145357ef921bde753e133062203
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868009"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Specificare IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un metodo o costruttore chiama uno o più membri con overload che accettano un <xref:System.IFormatProvider?displayProperty=fullName> parametro e il metodo o costruttore non chiama l'overload che accetta il <xref:System.IFormatProvider> parametro.

Questa regola ignora le chiamate ai metodi di .NET Framework che sono documentati come ignorando il <xref:System.IFormatProvider> parametro. La regola ignora anche i metodi seguenti:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descrizione della regola

Quando un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> o <xref:System.IFormatProvider> oggetto non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. Inoltre, i membri di .NET Framework scelgono le impostazioni cultura predefinite e formattazione basato su presupposti che potrebbero non essere corretti per il codice. Per assicurarsi che il codice funzioni come previsto per gli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

- Se il valore verrà visualizzato all'utente, usare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Se il valore verrà archiviato e utilizzato dal software (persistente in un file o database), usare le impostazioni cultura invarianti. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Se non si conosce la destinazione del valore, dispone al consumer di dati o provider di specificare le impostazioni cultura.

Anche se il comportamento predefinito del membro di overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che quest'ultima è autodocumentato e più facilmente gestibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, usare l'overload che accetta un <xref:System.IFormatProvider> argomento. In alternativa, usare una [c# stringa interpolata](/dotnet/csharp/tutorials/string-interpolation) e passarlo al <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> (metodo).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se si è certi che il formato predefinito è la scelta corretta e la gestibilità del codice non è una priorità di sviluppo importanti.

## <a name="example"></a>Esempio

Nel codice seguente, il `example1` stringa viola la regola CA1305. Il `example2` stringa soddisfa regola CA1305 passando <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, che implementa <xref:System.IFormatProvider>, a <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. Il `example3` stringa soddisfa regola CA1305 passando una stringa interpolata in <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>Regole correlate

- [CA1304: Specificare CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Vedere anche

- [Utilizzo della classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)