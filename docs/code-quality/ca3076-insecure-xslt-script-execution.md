---
title: 'CA3076: Esecuzione di script XSLT non protetta'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c6c5df0109a8cff3cefcc308ea27077ef0fbe03
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237082"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Esecuzione di script XSLT non protetta

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Se si esegue Extensible Stylesheets Language Transformations (XSLT) in applicazioni .NET in modo non protetto, il processore può risolvere i riferimenti URI non attendibili che potrebbero divulgare informazioni riservate a utenti malintenzionati causando attacchi Denial of Service e XSS. Per ulteriori informazioni, vedere la pagina relativa alle [considerazioni sulla sicurezza XSLT (guida. NET)](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Descrizione della regola

**XSLT** è uno standard W3C (World Wide Web Consortium) per la trasformazione dei dati XML. XSLT viene in genere usato per scrivere i fogli di stile per trasformare i dati XML in altri formati, ad esempio HTML, testo a lunghezza fissa, testo delimitato da virgole o formato XML diverso. Sebbene non sia consentito per impostazione predefinita, è possibile scegliere di abilitarlo per un progetto.

Per assicurarsi che non si stia esponendo una superficie di attacco, questa regola viene attivata ogni volta che XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> riceve istanze di combinazione non sicure <xref:System.Xml.XmlResolver>di e, che consente l'elaborazione di <xref:System.Xml.Xsl.XsltSettings> script dannosi.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Sostituire l'argomento XsltSettings non protetto con XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con un'istanza di che ha disabilitato l'esecuzione di script e funzioni di documento.

- Sostituire l'argomento <xref:System.Xml.XmlResolver> con Null o con un'istanza di <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Violazione che usa XsltSettings. TrustedXslt

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

### <a name="solution-that-uses-xsltsettingsdefault"></a>Soluzione che usa XsltSettings. default

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Funzione&mdash;del documento di violazione ed esecuzione di script non disabilitata

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Soluzione&mdash;disabilitare la funzione di documento e l'esecuzione di script

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

## <a name="see-also"></a>Vedere anche

- [Considerazioni sulla sicurezza XSLT (guida. NET)](/dotnet/standard/data/xml/xslt-security-considerations)