---
title: 'CA2301: Non chiamare BinaryFormatter.Deserialize senza aver prima impostato BinaryFormatter.Binder'
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
ms.openlocfilehash: d90ed71c1d5ca4cbfdcf8e500e1d176519a2fdff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037596"
---
# <a name="ca2301-do-not-call-binaryformatterdeserialize-without-first-setting-binaryformatterbinder"></a>CA2301: Non chiamare BinaryFormatter.Deserialize senza aver prima impostato BinaryFormatter.Binder

|||
|-|-|
|TypeName|DoNotCallBinaryFormatterDeserializeWithoutFirstSettingBinaryFormatterBinder|
|CheckId|CA2301|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Oggetto <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> metodo di deserializzazione è stato chiamato o cui viene fatto riferimento senza il <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> set di proprietà.

## <a name="rule-description"></a>Descrizione della regola

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Questa regola individua <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> deserializzazione chiamate ai metodi o i riferimenti, quando si <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> non ha relativo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> impostato. Se si vuole impedire qualsiasi deserializzazione con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> indipendentemente i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> proprietà, disabilitare questa regola e [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)e abilitare la regola [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, usare invece un serializzatore protetto e **non consente un utente malintenzionato di specificare un tipo arbitrario da deserializzare**. Alcuni serializzatori più sicure includono:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Non utilizzare mai <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se è necessario utilizzare un resolver di tipi, limitare tipi deserializzati da un elenco previsto.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET - usare TypeNameHandling.None. Se è necessario usare un altro valore per TypeNameHandling, limitare tipi deserializzati a un elenco con un ISerializationBinder personalizzato previsto.
  - Buffer del protocollo
- Rendere la prova di manomissione i dati serializzati. Dopo la serializzazione, firmare crittograficamente i dati serializzati. Prima della deserializzazione, la convalida della firma crittografica. Proteggere la chiave di crittografia la divulgazione e la progettazione per le rotazioni delle chiavi.
- Limitare i tipi deserializzati. Implementare una classe personalizzata <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Prima della deserializzazione con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, impostare il <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> proprietà a un'istanza di personalizzata <xref:System.Runtime.Serialization.SerializationBinder>. In sottoposto a override <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metodo, se non è previsto il tipo verrà generata un'eccezione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

### <a name="solution"></a>Soluzione

```csharp
using System;
using System.IO;
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Binary;

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

[Serializable]
public class BookRecord
{
    public string Title { get; set; }
    public string Author { get; set; }
    public int PageCount { get; set; }
    public AisleLocation Location { get; set; }
}

[Serializable]
public class AisleLocation
{
    public char Aisle { get; set; }
    public byte Shelf { get; set; }
}

public class ExampleClass
{
    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        formatter.Binder = new BookRecordSerializationBinder();
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) formatter.Deserialize(ms);
        }
    }
}
```

```vb
Imports System
Imports System.IO
Imports System.Runtime.Serialization
Imports System.Runtime.Serialization.Formatters.Binary

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

<Serializable()>
Public Class BookRecord
    Public Property Title As String
    Public Property Author As String
    Public Property Location As AisleLocation
End Class

<Serializable()>
Public Class AisleLocation
    Public Property Aisle As Char
    Public Property Shelf As Byte
End Class

Public Class ExampleClass
    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        formatter.Binder = New BookRecordSerializationBinder()
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(formatter.Deserialize(ms), BookRecord)
        End Using
    End Function
End Class
```

## <a name="related-rules"></a>Regole correlate

[CA2300: Non utilizzare il deserializzatore non sicuro BinaryFormatter](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)

[CA2302: BinaryFormatter. Binder prima che sia impostata la chiamata a BinaryFormatter](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)