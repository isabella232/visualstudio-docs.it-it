---
title: 'CA2310: Non utilizzare il deserializzatore non sicuro NetDataContractSerializer'
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
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135429"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: Non utilizzare il deserializzatore non sicuro NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|CheckId|CA2310|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Oggetto <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> metodo di deserializzazione è stato chiamato o cui si fa riferimento.

## <a name="rule-description"></a>Descrizione della regola

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Questa regola individua <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> riferimenti o chiamate al metodo di deserializzazione. Se si vogliono deserializzare solo quando la <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> viene impostata per limitare i tipi, disabilitare questa regola e abilitare regole [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) invece.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, usare invece un serializzatore protetto e **non consente un utente malintenzionato di specificare un tipo arbitrario da deserializzare**. Alcuni serializzatori più sicure includono:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Non utilizzare mai <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se è necessario utilizzare un resolver di tipi, limitare tipi deserializzati da un elenco previsto.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET - usare TypeNameHandling.None. Se è necessario usare un altro valore per TypeNameHandling, limitare tipi deserializzati a un elenco con un ISerializationBinder personalizzato previsto.
  - Buffer del protocollo
- Rendere la prova di manomissione i dati serializzati. Dopo la serializzazione, firmare crittograficamente i dati serializzati. Prima della deserializzazione, la convalida della firma crittografica. Proteggere la chiave di crittografia dal scoperte e progettazione per le rotazioni delle chiavi.
- Limitare i tipi deserializzati. Implementare una classe personalizzata <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Prima della deserializzazione con <xref:System.Runtime.Serialization.NetDataContractSerializer>, impostare il <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> proprietà a un'istanza di personalizzata <xref:System.Runtime.Serialization.SerializationBinder>. In sottoposto a override <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metodo, se il tipo è imprevisto, generare un'eccezione.
- Se si limitano i tipi deserializzati, è possibile disabilitare questa regola e abilitare regole [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Le regole [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) della Guida per assicurarsi che il <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> viene sempre impostata prima della deserializzazione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

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

[CA2311: Non deserializzare senza aver prima impostato NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: NetDataContractSerializer.Binder prima che sia impostata la deserializzazione](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
