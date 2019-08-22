---
title: 'CA2300: Non usare il deserializzatore non sicuro BinaryFormatter'
ms.date: 04/05/2019
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
- CA2300
- DoNotUseInsecureDeserializerBinaryFormatter
ms.openlocfilehash: 8a2bc2929b53843749d939f16057a11c0e944e33
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891216"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300: Non usare il deserializzatore non sicuro BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|CheckId|CA2300|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

È <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> stato chiamato o fatto riferimento A un metodo di deserializzazione.

## <a name="rule-description"></a>Descrizione della regola

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Questa regola trova <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> le chiamate al metodo di deserializzazione o i riferimenti. Se si desidera eseguire la deserializzazione solo quando <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> la proprietà è impostata su limita tipi, disabilitare questa regola e abilitare le regole [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) in alternativa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, usare invece un serializzatore protetto e **non consentire a un utente malintenzionato di specificare un tipo arbitrario da**deserializzare. Alcuni serializzatori più sicuri includono:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Non usare <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>mai. Se è necessario usare un resolver di tipi, limitare i tipi deserializzati a un elenco previsto.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-usare TypeNameHandling. None. Se è necessario usare un altro valore per TypeNameHandling, limitare i tipi deserializzati a un elenco previsto con un ISerializationBinder personalizzato.
  - Buffer del protocollo
- Eseguire la prova di manomissione dei dati serializzati. Dopo la serializzazione, la firma crittografica dei dati serializzati. Prima della deserializzazione, convalidare la firma crittografica. Proteggere la chiave crittografica da divulgare e progettare per le rotazioni delle chiavi.
- Limitare i tipi deserializzati. Implementare un oggetto <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>personalizzato. Prima di eseguire la deserializzazione <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> , impostare la proprietà su un'istanza <xref:System.Runtime.Serialization.SerializationBinder>di personalizzata. Nel metodo sottoposto <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> a override, se il tipo è imprevisto, generare un'eccezione per arrestare la deserializzazione.
  - Se si limitano i tipi deserializzati, potrebbe essere necessario disabilitare questa regola e abilitare le regole [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Le regole [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) consentono di garantire che <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> la proprietà sia sempre impostata prima della deserializzazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Regole correlate

[CA2301: Non chiamare BinaryFormatter. Deserialize senza prima impostare BinaryFormatter. Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Verificare che BinaryFormatter. Binder sia impostato prima di chiamare BinaryFormatter. Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)