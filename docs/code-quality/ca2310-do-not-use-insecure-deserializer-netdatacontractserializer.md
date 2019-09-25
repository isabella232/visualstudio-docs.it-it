---
title: 'CA2310: Non usare il deserializzatore non sicuro NetDataContractSerializer'
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
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: 5335e72307ea201ad77d6e59b267572d4d9aae56
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237716"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Non usare il deserializzatore non sicuro NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

È <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> stato chiamato o fatto riferimento A un metodo di deserializzazione.

## <a name="rule-description"></a>Descrizione della regola

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Questa regola trova <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> le chiamate al metodo di deserializzazione o i riferimenti. Se si desidera eseguire la deserializzazione solo quando <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> la proprietà è impostata su limita tipi, disabilitare questa regola e abilitare le regole [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) in alternativa.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, usare invece un serializzatore protetto e **non consentire a un utente malintenzionato di specificare un tipo arbitrario da deserializzare**. Alcuni serializzatori più sicuri includono:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Non usare <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>mai. Se è necessario usare un resolver di tipi, limitare i tipi deserializzati a un elenco previsto.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-usare TypeNameHandling. None. Se è necessario usare un altro valore per TypeNameHandling, limitare i tipi deserializzati a un elenco previsto con un ISerializationBinder personalizzato.
  - Buffer di protocollo
- Eseguire la prova di manomissione dei dati serializzati. Dopo la serializzazione, la firma crittografica dei dati serializzati. Prima della deserializzazione, convalidare la firma crittografica. Proteggere la chiave crittografica da divulgare e progettare per le rotazioni delle chiavi.
- Limitare i tipi deserializzati. Implementare un oggetto <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>personalizzato. Prima di eseguire la deserializzazione <xref:System.Runtime.Serialization.NetDataContractSerializer>con <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> , impostare la proprietà su un'istanza <xref:System.Runtime.Serialization.SerializationBinder>di personalizzata. Nel metodo sottoposto <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> a override, se il tipo è imprevisto, generare un'eccezione per arrestare la deserializzazione.
  - Se si limitano i tipi deserializzati, potrebbe essere necessario disabilitare questa regola e abilitare le regole [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Le regole [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) consentono di garantire che <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> la proprietà sia sempre impostata prima della deserializzazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Esempi di pseudo-codice

### <a name="violation"></a>Violazione

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Regole correlate

[CA2311: Non eseguire la deserializzazione senza prima impostare NetDataContractSerializer. Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Assicurarsi che NetDataContractSerializer. Binder sia impostato prima della deserializzazione](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
