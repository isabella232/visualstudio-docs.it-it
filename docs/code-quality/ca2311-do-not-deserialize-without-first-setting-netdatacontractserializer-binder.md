---
title: 'CA2311: Non deserializzare senza aver prima impostato NetDataContractSerializer.Binder'
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
- CA2311
- DoNotDeserializeWithoutFirstSettingNetDataContractSerializerBinder
ms.openlocfilehash: aec95d4bbd2d9bc498f9688c5601591d480d7f3b
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135439"
---
# <a name="ca2311-do-not-deserialize-without-first-setting-netdatacontractserializerbinder"></a>CA2311: Non deserializzare senza aver prima impostato NetDataContractSerializer.Binder

|||
|-|-|
|TypeName|DoNotDeserializeWithoutFirstSettingNetDataContractSerializerBinder|
|CheckId|CA2311|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Oggetto <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> metodo di deserializzazione è stato chiamato o cui viene fatto riferimento senza il <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> set di proprietà.

## <a name="rule-description"></a>Descrizione della regola

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Questa regola individua <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> deserializzazione chiamate ai metodi o i riferimenti, quando si <xref:System.Runtime.Serialization.NetDataContractSerializer> non ha relativo <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> impostato. Se si vuole impedire qualsiasi deserializzazione con <xref:System.Runtime.Serialization.NetDataContractSerializer> indipendentemente i <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> proprietà, disabilitare questa regola e [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)e abilitare la regola [CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md).

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

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Soluzione

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;

public class BookRecordSerializationBinder : SerializationBinder
{
    public override Type BindToType(string assemblyName, string typeName)
    {
        // One way to discover expected types is through testing deserialization
        // of **valid** data and logging the types used.

        ////Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')");

        if (typeName == "BookRecord" || typeName == "AisleLocation")
        {
            return null;
        }
        else
        {
            throw new ArgumentException("Unexpected type", nameof(typeName));
        }
    }
}

[DataContract]
public class BookRecord
{
    [DataMember]
    public string Title { get; set; }

    [DataMember]
    public string Author { get; set; }

    [DataMember]
    public int PageCount { get; set; }

    [DataMember]
    public AisleLocation Location { get; set; }
}

[DataContract]
public class AisleLocation
{
    [DataMember]
    public char Aisle { get; set; }

    [DataMember]
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        serializer.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) serializer.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization

Public Class BookRecordSerializationBinder
    Inherits SerializationBinder

    Public Overrides Function BindToType(assemblyName As String, typeName As String) As Type
        ' One way to discover expected types is through testing deserialization
        ' of **valid** data and logging the types used.

        'Console.WriteLine($"BindToType('{assemblyName}', '{typeName}')")

        If typeName = "BinaryFormatterVB.BookRecord" Or typeName = "BinaryFormatterVB.AisleLocation" Then
            Return Nothing
        Else
            Throw New ArgumentException("Unexpected type", NameOf(typeName))
        End If
    End Function
End Class

<DataContract()>
Public Class BookRecord
    <DataMember()>
    Public Property Title As String

    <DataMember()>
    Public Property Author As String

    <DataMember()>
    Public Property Location As AisleLocation
End Class

<DataContract()>
Public Class AisleLocation
    <DataMember()>
    Public Property Aisle As Char

    <DataMember()>
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        serializer.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(serializer.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Regole correlate

[CA2310: Non utilizzare il deserializzatore non sicuro NetDataContractSerializer](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)

[CA2312: NetDataContractSerializer.Binder prima che sia impostata la deserializzazione](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)