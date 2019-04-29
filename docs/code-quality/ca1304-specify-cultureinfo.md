---
title: 'CA1304: Specificare CultureInfo'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1fe4ebce3a49c4aa626515e22eacd1c8e263847
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797505"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Specificare CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa

Un metodo o costruttore chiama un membro che ha un overload che accetta un <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> parametro e il metodo o costruttore non chiama l'overload che accetta il <xref:System.Globalization.CultureInfo> parametro. Questa regola ignora le chiamate ai metodi seguenti:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descrizione della regola

Quando un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider?displayProperty=nameWithType> oggetto non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. Inoltre, i membri di .NET Framework scelgono le impostazioni cultura predefinite e formattazione basato su presupposti che potrebbero non essere corretti per il codice. Per verificare che il codice funzioni come previsto per gli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

- Se il valore verrà visualizzato all'utente, usare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Se il valore verrà archiviato e utilizzato dal software, vale a dire, mantenuto in un file o database, usare le impostazioni cultura invarianti. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Se non si conosce la destinazione del valore, dispone al consumer di dati o provider di specificare le impostazioni cultura.

Anche se il comportamento predefinito del membro di overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che quest'ultima è autodocumentato e più facilmente gestibili.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> viene usato solo per recuperare le risorse localizzate con un'istanza del <xref:System.Resources.ResourceManager?displayProperty=nameWithType> classe.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, usare l'overload che accetta un <xref:System.Globalization.CultureInfo> argomento.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da questa regola se si è certi che la lingua predefinita è la scelta corretta e la gestibilità del codice non è una priorità di sviluppo importanti.

## <a name="example-showing-how-to-fix-violations"></a>Esempio che illustra come correggere le violazioni

Nell'esempio seguente, `BadMethod` fa sì che due delle violazioni di questa regola. `GoodMethod` corregge la prima violazione passando a impostazioni cultura invarianti <xref:System.String.Compare%2A?displayProperty=nameWithType>e consente di correggere la violazione secondo passando le impostazioni cultura correnti <xref:System.String.ToLower%2A?displayProperty=nameWithType> perché `string3` viene visualizzato all'utente.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Visualizzazione di esempio l'output formattato

Nell'esempio seguente mostra l'effetto delle impostazioni cultura correnti sul valore predefinito <xref:System.IFormatProvider> sarà selezionata per il <xref:System.DateTime> tipo.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Questo esempio produce il seguente output:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Regole correlate

- [CA1305: Specificare IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Vedere anche

- [Utilizzo della classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)