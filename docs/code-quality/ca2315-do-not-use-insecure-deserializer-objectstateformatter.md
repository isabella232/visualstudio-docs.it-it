---
title: 'CA2315: Non usare il deserializzatore non sicuro ObjectStateFormatter'
ms.date: 05/01/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2315
- DoNotUseInsecureDeserializerObjectStateFormatter
ms.openlocfilehash: 30e9d55fa5aa9c909c29935988f76107a4b5556d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237678"
---
# <a name="ca2315-do-not-use-insecure-deserializer-objectstateformatter"></a>CA2315: Non usare il deserializzatore non sicuro ObjectStateFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerObjectStateFormatter|
|CheckId|CA2315|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

È <xref:System.Web.UI.ObjectStateFormatter?displayProperty=nameWithType> stato chiamato o fatto riferimento A un metodo di deserializzazione.

## <a name="rule-description"></a>Descrizione della regola

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Questa regola trova <xref:System.Web.UI.ObjectStateFormatter?displayProperty=nameWithType> le chiamate al metodo di deserializzazione o i riferimenti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

[!INCLUDE[insecure-deserializers-fixes-for-always-insecure-deserializers](includes/insecure-deserializers-fixes-for-always-insecure-deserializers-md.md)]

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System.IO;
using System.Web.UI;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        ObjectStateFormatter formatter = new ObjectStateFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Web.UI

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As ObjectStateFormatter = New ObjectStateFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```