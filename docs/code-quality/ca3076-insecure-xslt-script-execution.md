---
title: 'CA3076: Esecuzione di script XSLT non protetta'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74fe556d775e60dec5dde4528a1924e55ab4c2ed
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546392"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: Esecuzione di script XSLT non protetta

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Se si esegue Extensible Stylesheets Language Transformations (XSLT) in applicazioni .NET in modo non protetto, il processore può risolvere i riferimenti URI non attendibili che potrebbero divulgare informazioni riservate a utenti malintenzionati causando attacchi Denial of Service e XSS. Per altre informazioni, vedere [Considerations(.NET Guide) sicurezza XSLT](/dotnet/standard/data/xml/xslt-security-considerations).

## <a name="rule-description"></a>Descrizione della regola

**XSLT** è uno standard di World Wide Web Consortium (W3C) per la trasformazione dei dati XML. XSLT è in genere utilizzato per scrivere i fogli di stile per trasformare i dati XML in altri formati, ad esempio HTML, testo di lunghezza fissa, testo delimitato da virgole o un altro formato XML. Sebbene non sia consentito per impostazione predefinita, è possibile scegliere di abilitarlo per un progetto.

Per assicurarsi che non si espone una superficie di attacco, questa regola viene attivata ogni volta che il XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> istanze di combinazione non protetta di riceve <xref:System.Xml.Xsl.XsltSettings> e <xref:System.Xml.XmlResolver>, che consente l'elaborazione di uno script dannoso.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Sostituire l'argomento XsltSettings non protetto con XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> o con un'istanza che ha disabilitato l'esecuzione di script e funzioni di documento.

- Sostituire l'argomento <xref:System.Xml.XmlResolver> con Null o con un'istanza di <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation-that-uses-xsltsettingstrustedxslt"></a>Violazione che usa XsltSettings.TrustedXslt

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

### <a name="solution-that-uses-xsltsettingsdefault"></a>Soluzione che usa XsltSettings.Default

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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>Violazione&mdash;documentare l'esecuzione di script e funzioni non disabilitata

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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>Soluzione&mdash;disabilitare l'esecuzione di script e funzioni di documento

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

- [Considerazioni sulla sicurezza XSLT (Guida per .NET)](/dotnet/standard/data/xml/xslt-security-considerations)