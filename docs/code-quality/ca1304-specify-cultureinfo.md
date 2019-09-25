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
ms.openlocfilehash: 2539cef9e6b2fe20513943f686aeaa1ff7a79013
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235096"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: Specificare CultureInfo

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Category|Microsoft. globalizzazione|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Un metodo o un costruttore chiama un membro che dispone di un overload che <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> accetta un parametro e il metodo o il costruttore non chiama l'overload che accetta <xref:System.Globalization.CultureInfo> il parametro. Questa regola consente di ignorare le chiamate ai metodi seguenti:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Descrizione della regola

Quando un <xref:System.Globalization.CultureInfo> oggetto <xref:System.IFormatProvider?displayProperty=nameWithType> o non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. Inoltre, i membri .NET scelgono le impostazioni cultura predefinite e la formattazione in base a presupposti che potrebbero non essere corretti per il codice. Per assicurarsi che il codice funzioni come previsto per gli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

- Se il valore verrà visualizzato all'utente, utilizzare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Se il valore verrà archiviato e accessibile dal software, ovvero salvato in modo permanente in un file o un database, utilizzare la lingua inglese. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Se non si conosce la destinazione del valore, chiedere al consumer o al provider di dati di specificare le impostazioni cultura.

Anche se il comportamento predefinito del membro in overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che il codice sia autodocumentato e più facilmente gestibile.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>viene usato solo per recuperare le risorse localizzate usando un'istanza della <xref:System.Resources.ResourceManager?displayProperty=nameWithType> classe.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, usare l'overload che accetta un <xref:System.Globalization.CultureInfo> argomento.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

È possibile eliminare un avviso da questa regola quando si è certi che le impostazioni cultura predefinite sono la scelta corretta e dove la gestibilità del codice non è una priorità di sviluppo importante.

## <a name="example-showing-how-to-fix-violations"></a>Esempio che illustra come correggere le violazioni

Nell'esempio seguente, `BadMethod` causa due violazioni di questa regola. `GoodMethod`corregge la prima violazione passando le impostazioni cultura invarianti a <xref:System.String.Compare%2A?displayProperty=nameWithType>e corregge la seconda violazione passando le impostazioni cultura correnti a <xref:System.String.ToLower%2A?displayProperty=nameWithType> perché `string3` viene visualizzato all'utente.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Esempio che mostra l'output formattato

Nell'esempio seguente viene illustrato l'effetto delle impostazioni cultura correnti sul <xref:System.IFormatProvider> valore predefinito selezionato <xref:System.DateTime> dal tipo.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Questo esempio produce il seguente output:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Regole correlate

- [CA1305: Specifica IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Vedere anche

- [Uso della classe CultureInfo](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)