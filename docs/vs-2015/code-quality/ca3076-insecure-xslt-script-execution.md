---
title: 'CA3076: esecuzione di script XSLT non protetta | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b3e06bb7a150c4bb07eefc0571818f1127fe460
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545119"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Esecuzione di script XSLT non protetta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Se si esegue [Extensible Stylesheets Language Transformations (XSLT)](https://support.microsoft.com/kb/313997) in applicazioni .NET in modo non protetto, il processore può [risolvere i riferimenti URI non attendibili](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) che potrebbero divulgare informazioni riservate a utenti malintenzionati, causando attacchi Denial of Service e tra siti.

## <a name="rule-description"></a>Descrizione della regola
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) è uno standard W3C (World Wide Web Consortium) per la trasformazione dei dati XML. XSLT viene in genere usato per scrivere i fogli di stile per trasformare i dati XML in altri formati, ad esempio HTML, testo di lunghezza fissa, testo delimitato da virgole, oppure in un altro formato XML. Sebbene non sia consentito per impostazione predefinita, è possibile scegliere di abilitarlo per un progetto.

 Per assicurarsi che non si stia esponendo una superficie di attacco, questa regola viene attivata ogni volta che XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> riceve istanze di combinazione non sicure di <xref:System.Xml.Xsl.XsltSettings> e <xref:System.Xml.XmlResolver> , che consente l'elaborazione di script dannosi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Sostituire l'argomento XsltSettings non protetto con XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con un'istanza di che ha disabilitato l'esecuzione di script e funzioni di documento.

- Sostituire l'argomento <xref:System.Xml.XmlResolver> con Null o con un'istanza di <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
} 
```

### <a name="solution"></a>Soluzione

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violation"></a>Violazione

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```
