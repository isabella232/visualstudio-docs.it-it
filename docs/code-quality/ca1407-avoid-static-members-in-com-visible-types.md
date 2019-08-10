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
ms.openlocfilehash: 631be1a93318cd24af4251fefbc710294fa52bf7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922006"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Evitare i membri statici nei tipi visibili a COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
Un tipo contrassegnato in modo specifico come visibile a Component Object Model (com) contiene un `public``static` metodo.

## <a name="rule-description"></a>Descrizione della regola
COM non supporta `static` i metodi.

Questa regola ignora le funzioni di accesso a proprietà e eventi, i metodi di overload degli operatori o i <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> metodi contrassegnati con l'attributo o l'attributo.

Per impostazione predefinita, i seguenti elementi sono visibili a COM: assembly, tipi pubblici, membri di istanze pubbliche nei tipi pubblici e tutti i membri dei tipi di valore pubblici.

Affinché questa regola si verifichi, è necessario impostare un <xref:System.Runtime.InteropServices.ComVisibleAttribute> livello di assembly su `false` e la classe- <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve essere impostata su `true`, come illustrato nel codice seguente.

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
Per correggere una violazione di questa regola, modificare la progettazione in modo da usare un metodo di istanza che fornisce la stessa `static` funzionalità del metodo.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se un client com non richiede l'accesso alla funzionalità fornita dal `static` metodo.

## <a name="example-violation"></a>Violazione di esempio

### <a name="description"></a>Descrizione
Nell'esempio seguente viene illustrato `static` un metodo che viola questa regola.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Commenti
In questo esempio non è possibile chiamare il metodo **book. FromPages** da com.

## <a name="example-fix"></a>Correzione di esempio

### <a name="description"></a>Descrizione
Per correggere la violazione nell'esempio precedente, è possibile modificare il metodo in un metodo di istanza, ma ciò non ha senso in questa istanza. Una soluzione migliore consiste nell'applicare `ComVisible(false)` in modo esplicito al metodo per rendere chiaro ad altri sviluppatori che il metodo non può essere visualizzato da com.

Nell'esempio seguente viene <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> applicato al metodo.

### <a name="code"></a>Codice
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1017 Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

[CA1406: Evitare gli argomenti Int64 per Visual Basic 6 client](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

[CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Vedere anche
[Interoperabilità con codice non gestito](/dotnet/framework/interop/index)