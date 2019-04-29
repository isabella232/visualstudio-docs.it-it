---
title: 'CA3075: Elaborazione DTD non protetta'
ms.date: 03/18/2019
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de817e3aaecbdd1c89cc2174e91126ea39d99d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541117"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Elaborazione DTD non protetta

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Se si usano istanze di <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> non protette o si fa riferimento a origini di entità esterne, il parser può accettare un input non attendibile e divulgare informazioni riservate a utenti malintenzionati.

## <a name="rule-description"></a>Descrizione della regola

La *definizione DTD (Document Type Definition)* rappresenta uno dei due modi in cui un parser XML può determinare la validità di un documento, come definito dalla raccomandazione  [W3C (World Wide Web Consortium) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Questa regola cerca le proprietà e le istanze in cui vengono accettati i dati non attendibili per avvisare gli sviluppatori potenziale [divulgazione](/dotnet/framework/wcf/feature-details/information-disclosure) minacce o [Denial of Service (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) attacchi. Questa regola viene attivata quando:

- DtdProcessing viene abilitato nell'istanza di <xref:System.Xml.XmlReader> , che risolve le entità XML esterne con <xref:System.Xml.XmlUrlResolver>.

- La proprietà <xref:System.Xml.XmlNode.InnerXml%2A> nel codice XML è impostata.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> viene impostata su Parse.

- Non attendibile l'input viene elaborato utilizzando <xref:System.Xml.XmlResolver> invece di <xref:System.Xml.XmlSecureResolver>.

- Il <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metodo viene richiamato con un <xref:System.Xml.XmlReaderSettings> istanza o senza alcuna istanza.

- <xref:System.Xml.XmlReader> viene creato con le impostazioni predefinite non protette o valori.

In ognuno di questi casi, il risultato è lo stesso: i contenuti da entrambi le condivisioni file di sistema o rete dal computer in cui viene elaborato il codice XML è esposta a un utente malintenzionato o l'elaborazione della DTD può essere usato come vettore di attacchi DoS.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Rilevare ed elaborare tutte le eccezioni XmlTextReader correttamente per evitare la divulgazione di informazioni di percorso.

- Usare il <xref:System.Xml.XmlSecureResolver> per limitare le risorse che può accedere XmlTextReader.

- Non consentire all'oggetto <xref:System.Xml.XmlReader> di aprire risorse esterne impostando la proprietà <xref:System.Xml.XmlResolver> su **Null**.

- Verificare che il <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A?displayProperty=nameWithType> proprietà viene assegnato da un'origine attendibile.

**.NET 3.5 e versioni precedenti**

- Disabilitare l'elaborazione DTD se usano origini non attendibili impostando la <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> proprietà **true**.

- La classe XmlTextReader ha una richiesta di ereditarietà con attendibilità totale.

**.NET 4 e versioni successive**

- Evitare di abilitare DtdProcessing se usano origini non attendibili impostando la <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> proprietà **Prohibit** oppure **ignora**.

- Assicurarsi che il metodo Load() accetti un'istanza di XmlReader ovunque venga usato InnerXml.

> [!NOTE]
> Questa regola potrebbe segnalare dei falsi positivi in alcune istanze valide di XmlSecureResolver.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Violazione

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Violazioni

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlReader reader = XmlReader.Create(sreader, new XmlReaderSettings() { XmlResolver = null });
    doc.Load(reader);
}
```

### <a name="violation"></a>Violazione

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlReader reader = XmlReader.Create(stream, new XmlReaderSettings() { XmlResolver = null });
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Violazione

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlReader reader = XmlReader.Create(path, new XmlReaderSettings() { XmlResolver = null });
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Violazione

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Violazioni

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings() { XmlResolver = null };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```
