---
title: 'CA1407: evitare i membri statici nei tipi visibili a COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6996d210417a56dd83532c481aaa0dc80b9f23ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655244"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Evitare i membri statici nei tipi visibili a COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un tipo contrassegnato in modo specifico come visibile a Component Object Model (COM) contiene un metodo `public``static`.

## <a name="rule-description"></a>Descrizione della regola
 COM non supporta i metodi `static`.

 Questa regola ignora le funzioni di accesso a proprietà e eventi, i metodi di overload degli operatori o i metodi contrassegnati utilizzando l'attributo <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o l'attributo <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

 Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanze pubbliche nei tipi pubblici e tutti i membri dei tipi di valore pubblici.

 Per eseguire questa regola, è necessario che un <xref:System.Runtime.InteropServices.ComVisibleAttribute> a livello di assembly sia impostato su `false` e che la classe-<xref:System.Runtime.InteropServices.ComVisibleAttribute> sia impostata su `true`, come illustrato nel codice seguente.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare la progettazione in modo da usare un metodo di istanza che fornisce la stessa funzionalità del metodo `static`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se un client COM non richiede l'accesso alla funzionalità fornita dal metodo `static`.

## <a name="example-violation"></a>Violazione di esempio

### <a name="description"></a>Descrizione
 Nell'esempio seguente viene illustrato un metodo `static` che viola questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Comments
 In questo esempio non è possibile chiamare il metodo **book. FromPages** da com.

## <a name="example-fix"></a>Correzione di esempio

### <a name="description"></a>Descrizione
 Per correggere la violazione nell'esempio precedente, è possibile modificare il metodo in un metodo di istanza, ma ciò non ha senso in questa istanza. Una soluzione migliore consiste nell'applicare in modo esplicito `ComVisible(false)` al metodo per rendere chiaro ad altri sviluppatori che il metodo non può essere visualizzato da COM.

 Nell'esempio seguente viene applicato <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> al metodo.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
