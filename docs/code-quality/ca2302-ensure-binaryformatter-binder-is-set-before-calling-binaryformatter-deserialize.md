---
title: 'CA2302: BinaryFormatter. Binder prima che sia impostata la chiamata a BinaryFormatter'
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
ms.openlocfilehash: fb997d8184ea9459b46eee95bfe2863e8c1c6ed0
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59367289"
---
# <a name="ca2302-ensure-binaryformatterbinder-is-set-before-calling-binaryformatterdeserialize"></a>CA2302: BinaryFormatter. Binder prima che sia impostata la chiamata a BinaryFormatter

|||
|-|-|
|TypeName|EnsureBinaryFormatterBinderIsSetBeforeCallingBinaryFormatterDeserialize|
|CheckId|CA2302|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Oggetto <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> metodo di deserializzazione è stato chiamato o cui si fa riferimento e il <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> proprietà può essere null.

## <a name="rule-description"></a>Descrizione della regola

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Questa regola individua <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> chiamate al metodo o i riferimenti di deserializzazione quando <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> quando relativo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> potrebbe essere null. Se si vuole impedire qualsiasi deserializzazione con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> indipendentemente i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> proprietà, disabilitare questa regola e [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)e abilitare la regola [CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Se possibile, usare invece un serializzatore protetto e **non consente un utente malintenzionato di specificare un tipo arbitrario da deserializzare**. Alcuni serializzatori più sicure includono:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Non utilizzare mai <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Se è necessario utilizzare un resolver di tipi, è necessario limitare tipi deserializzati da un elenco previsto.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET - usare TypeNameHandling.None. Se è necessario usare un altro valore per TypeNameHandling, è necessario limitare i tipi deserializzati da un elenco previsto.
  - Buffer del protocollo
- Rendere i dati serializzati di prova di manomissione. Dopo la serializzazione, firmare crittograficamente i dati serializzati. Prima della deserializzazione, la convalida della firma crittografica. È necessario proteggere la chiave di crittografia da scoperte e deve progettare per le rotazioni delle chiavi.
- Limitare i tipi deserializzati. Implementare una classe personalizzata <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Prima della deserializzazione con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, impostare il <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> proprietà a un'istanza di personalizzata <xref:System.Runtime.Serialization.SerializationBinder>. In sottoposto a override <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metodo, se non è previsto il tipo verrà generata un'eccezione.
  - Assicurarsi che tutti i percorsi del codice dispongano di <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> set di proprietà.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

- È possibile eliminare un avviso da questa regola se si conosce che l'input è considerato attendibile. È consigliabile che i flussi di dati e i limiti di attendibilità dell'applicazione possono cambiare nel tempo.
- È possibile eliminare questo avviso se è stata acquisita una delle precauzioni di cui sopra.

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
    public BinaryFormatter Formatter { get; set; }

    public BookRecord DeserializeBookRecord(byte[] bytes)
    {
        using (MemoryStream ms = new MemoryStream(bytes))
        {
            return (BookRecord) this.Formatter.Deserialize(ms);
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
    Public Property Formatter As BinaryFormatter

    Public Function DeserializeBookRecord(bytes As Byte()) As BookRecord
        Using ms As MemoryStream = New MemoryStream(bytes)
            Return CType(Me.Formatter.Deserialize(ms), BookRecord)
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
            throw new ArgumentException("Unexpected type", "typeName");
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
            Throw New ArgumentException("Unexpected type", "typeName")
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

[CA2301: Non chiamare BinaryFormatter senza aver prima impostato BinaryFormatter. Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)
