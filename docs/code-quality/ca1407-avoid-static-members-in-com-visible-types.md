---
title: 'CA1407: Evitare i membri statici nei tipi visibili a COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ea59bee887948fcb9fe293af338f49bfb9f8dfc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444215"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Evitare i membri statici nei tipi visibili a COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft. interoperabilità|
|Modifica|Senza interruzioni|

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

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se un client COM non richiede l'accesso alla funzionalità fornita dal metodo `static`.

## <a name="example-violation"></a>Violazione di esempio

### <a name="description"></a>Descrizione
Nell'esempio seguente viene illustrato un metodo `static` che viola questa regola.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Comments
In questo esempio non è possibile chiamare il metodo **book. FromPages** da com.

## <a name="example-fix"></a>Correzione di esempio

### <a name="description"></a>Descrizione
Per correggere la violazione nell'esempio precedente, è possibile modificare il metodo in un metodo di istanza, ma ciò non ha senso in questa istanza. Una soluzione migliore consiste nell'applicare in modo esplicito `ComVisible(false)` al metodo per rendere chiaro ad altri sviluppatori che il metodo non può essere visualizzato da COM.

Nell'esempio seguente viene applicato <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> al metodo.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

[CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

[CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Vedere anche
[Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
