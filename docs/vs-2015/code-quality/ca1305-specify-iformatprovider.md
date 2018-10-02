---
title: 'CA1305: Specificare IFormatProvider | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8d4d187383a139198cbdbcf1ebf8d69338450959
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589288"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: Specificare IFormatProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1305: Specificare IFormatProvider](https://docs.microsoft.com/visualstudio/code-quality/ca1305-specify-iformatprovider).

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Category|Microsoft.Globalization|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo o costruttore chiama uno o più membri con overload che accettano un <xref:System.IFormatProvider?displayProperty=fullName> parametro e il metodo o costruttore non chiama l'overload che accetta il <xref:System.IFormatProvider> parametro. Questa regola ignora le chiamate a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] metodi documentati come ignorando il <xref:System.IFormatProvider> parametro e inoltre i metodi seguenti:

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Descrizione della regola
 Quando un <xref:System.Globalization.CultureInfo?displayProperty=fullName> o <xref:System.IFormatProvider> oggetto non viene specificato, il valore predefinito fornito dal membro di overload potrebbe non avere l'effetto desiderato in tutte le impostazioni locali. Inoltre, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] membri scelgono le impostazioni cultura predefinite e la formattazione basato su presupposti che potrebbero non essere corretti per il codice. Per assicurarsi che il codice funzioni come previsto per gli scenari, è necessario fornire informazioni specifiche delle impostazioni cultura in base alle linee guida seguenti:

-   Se il valore verrà visualizzato all'utente, usare le impostazioni cultura correnti. Vedere <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

-   Se il valore verrà archiviato e utilizzato dal software (persistente in un file o database), usare le impostazioni cultura invarianti. Vedere <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

-   Se non si conosce la destinazione del valore, dispone al consumer di dati o provider di specificare le impostazioni cultura.

 Si noti che <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> viene usato solo per recuperare le risorse localizzate con un'istanza del <xref:System.Resources.ResourceManager?displayProperty=fullName> classe.

 Anche se il comportamento predefinito del membro di overload è adatto alle proprie esigenze, è preferibile chiamare in modo esplicito l'overload specifico delle impostazioni cultura in modo che quest'ultima è autodocumentato e più facilmente gestibili.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, usare l'overload che accetta un <xref:System.Globalization.CultureInfo> o <xref:System.IFormatProvider> e specificare l'argomento in base alle linee guida elencate in precedenza.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se si è certi che il provider di impostazioni cultura o il formato predefinito è la scelta corretta e in cui la gestibilità del codice non è una priorità di sviluppo importanti.

## <a name="example"></a>Esempio
 Nell'esempio seguente, `BadMethod` fa sì che due delle violazioni di questa regola. `GoodMethod` corregge la prima violazione passando a impostazioni cultura invarianti <xref:System.String.Compare%2A>e consente di correggere la violazione secondo passando le impostazioni cultura correnti <xref:System.String.ToLower%2A> perché `string3` viene visualizzato all'utente.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra l'effetto delle impostazioni cultura correnti sul valore predefinito <xref:System.IFormatProvider> sarà selezionata per il <xref:System.DateTime> tipo.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Questo esempio produce il seguente output:

 **4/6/1900:12 12.15**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Regole correlate
 [CA1304: Specificare CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Vedere anche
 [NIB: Uso della classe CultureInfo](http://msdn.microsoft.com/en-us/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)



