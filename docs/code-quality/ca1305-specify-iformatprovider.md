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
ms.openlocfilehash: a9f6c8fd44749de43d86bf8037df0130ad682321
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235040"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Specificare IFormatProvider

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft. globalizzazione|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un metodo o un costruttore chiama uno o più membri con overload che accettano un <xref:System.IFormatProvider?displayProperty=fullName> parametro e il metodo o il costruttore non chiama l'overload che accetta il <xref:System.IFormatProvider> parametro.

Questa regola ignora le chiamate ai metodi .NET documentati come ignorando il <xref:System.IFormatProvider> parametro. La regola ignora inoltre i metodi seguenti:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descrizione della regola

Quando un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> oggetto <xref:System.IFormatProvider> o non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. Inoltre, i membri .NET scelgono le impostazioni cultura predefinite e la formattazione in base a presupposti che potrebbero non essere corretti per il codice. Per assicurarsi che il codice funzioni come previsto per gli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

- Se il valore verrà visualizzato all'utente, utilizzare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Se il valore verrà archiviato e accessibile dal software (reso permanente in un file o un database), usare la lingua inglese. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Se non si conosce la destinazione del valore, chiedere al consumer o al provider di dati di specificare le impostazioni cultura.

Anche se il comportamento predefinito del membro in overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che il codice sia autodocumentato e più facilmente gestibile.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, usare l'overload che accetta un <xref:System.IFormatProvider> argomento. In alternativa, usare una [ C# stringa interpolata](/dotnet/csharp/tutorials/string-interpolation) e passarla <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> al metodo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola quando è certo che il formato predefinito è la scelta corretta e dove la gestibilità del codice non è una priorità di sviluppo importante.

## <a name="example"></a>Esempio

Nel codice seguente la stringa viola `example1` la regola CA1305. La `example2` stringa soddisfa la regola CA1305 passando <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, che implementa <xref:System.IFormatProvider>, a <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. La `example3` stringa soddisfa la regola CA1305 passando una stringa interpolata a <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

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

- [Uso della classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)