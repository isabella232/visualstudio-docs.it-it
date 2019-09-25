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
ms.openlocfilehash: 42efb51dfe9c447538fe8f01bdd37c73bf993d8f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237114"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Elaborazione DTD non protetta

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Se si usano istanze di <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> non protette o si fa riferimento a origini di entità esterne, il parser può accettare un input non attendibile e divulgare informazioni riservate a utenti malintenzionati.

## <a name="rule-description"></a>Descrizione della regola

La *definizione DTD (Document Type Definition)* rappresenta uno dei due modi in cui un parser XML può determinare la validità di un documento, come definito dalla raccomandazione  [W3C (World Wide Web Consortium) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Questa regola cerca le proprietà e le istanze in cui vengono accettati i dati non attendibili per avvisare gli sviluppatori sulle potenziali minacce per la [divulgazione di informazioni](/dotnet/framework/wcf/feature-details/information-disclosure) o attacchi [Denial of Service (DOS)](/dotnet/framework/wcf/feature-details/denial-of-service) . Questa regola viene attivata quando:

- DtdProcessing viene abilitato nell'istanza di <xref:System.Xml.XmlReader> , che risolve le entità XML esterne con <xref:System.Xml.XmlUrlResolver>.

- La proprietà <xref:System.Xml.XmlNode.InnerXml%2A> nel codice XML è impostata.

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>la proprietà è impostata su Parse.

- L'input non attendibile viene elaborato <xref:System.Xml.XmlResolver> con <xref:System.Xml.XmlSecureResolver>anziché con.

- Il <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metodo viene richiamato con un'istanza <xref:System.Xml.XmlReaderSettings> non protetta o senza alcuna istanza.

- <xref:System.Xml.XmlReader>viene creato con impostazioni o valori predefiniti non sicuri.

In ognuno di questi casi, il risultato è lo stesso: il contenuto del file system o delle condivisioni di rete del computer in cui viene elaborato il codice XML verrà esposto all'autore dell'attacco oppure l'elaborazione della DTD può essere usata come vettore DoS.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Rilevare ed elaborare correttamente tutte le eccezioni XmlTextReader per evitare la divulgazione di informazioni sul percorso.

- <xref:System.Xml.XmlSecureResolver> Usare per limitare le risorse a cui XmlTextReader può accedere.

- Non consentire all'oggetto <xref:System.Xml.XmlReader> di aprire risorse esterne impostando la proprietà <xref:System.Xml.XmlResolver> su **Null**.

- Verificare che la <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A?displayProperty=nameWithType> proprietà sia assegnata da un'origine attendibile.

**.NET 3,5 e versioni precedenti**

- Disabilitare l'elaborazione DTD se si gestiscono origini non attendibili impostando la <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> proprietà su **true**.

- La classe XmlTextReader ha una richiesta di ereditarietà con attendibilità totale.

**.NET 4 e versioni successive**

- Evitare di abilitare DtdProcessing se si usano origini non attendibili impostando la <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> proprietà su **Impedisci** o **Ignora**.

- Assicurarsi che il metodo Load() accetti un'istanza di XmlReader ovunque venga usato InnerXml.

> [!NOTE]
> Questa regola potrebbe segnalare dei falsi positivi in alcune istanze valide di XmlSecureResolver.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

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
