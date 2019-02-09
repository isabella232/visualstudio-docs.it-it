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
ms.openlocfilehash: 5b09122aebdc02b9eacb32df596914a0a08a9ea9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932679"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Evitare i membri statici nei tipi visibili a COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un tipo contrassegnato specificatamente come visibile al modello COM (Component Object) contiene un `public``static` (metodo).

## <a name="rule-description"></a>Descrizione della regola
 COM non supporta `static` metodi.

 Questa regola ignora proprietà e queste funzioni, operatori di overload di metodi o i metodi contrassegnati con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attributo o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attributo.

 Per impostazione predefinita, sono visibili a COM seguente: assembly, i tipi pubblici, i membri di istanza pubblici nei tipi pubblici e tutti i membri dei tipi di valore pubblico.

 Per questa regola si verifica quando un livello di assembly <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve essere impostata su `false` e la classe - <xref:System.Runtime.InteropServices.ComVisibleAttribute> deve essere impostata su `true`, come illustrato nel codice seguente.

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
 Per correggere una violazione di questa regola, modificare la progettazione per utilizzare un metodo di istanza che fornisce la stessa funzionalità di `static` (metodo).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola se un client COM non richiede l'accesso alla funzionalità fornita dal `static` (metodo).

## <a name="example-violation"></a>Esempio di violazione

### <a name="description"></a>Descrizione
 L'esempio seguente mostra un `static` metodo che violano questa regola.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Commenti
 In questo esempio, il **Book. FromPages** metodo non può essere chiamato da COM.

## <a name="example-fix"></a>Correzione di esempio

### <a name="description"></a>Descrizione
 Per correggere la violazione dell'esempio precedente, è possibile cambiare il metodo a un metodo di istanza, ma che non ha senso in questa istanza. Una soluzione migliore consiste nell'applicare in modo esplicito `ComVisible(false)` al metodo per indicare chiaramente all'altri sviluppatori che il metodo non può essere visibile da COM.

 L'esempio seguente applica <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> al metodo.

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Evitare gli argomenti Int64 per i client Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)