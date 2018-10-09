---
title: 'CA3077: Elaborazione non sicura in Progettazione API, documenti XML e lettori di testo XML | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 175d655c2283dfe764564d42b6893b12d1f09e22
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589980"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Elaborazione non sicura in progettazione API, documenti XML e lettori di testo XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA3077: elaborazione non sicura in Progettazione API, documenti XML e lettori di testo XML](https://docs.microsoft.com/visualstudio/code-quality/ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader).

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Quando si progetta un'API derivata da XMLDocument e XMLTextReader, tenere presente <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Se si usano istanze di DTDProcessing non protette per fare riferimento o risolvere origini di entità esterne oppure per impostare valori non protetti nel codice XML, si può causare la divulgazione di informazioni.

## <a name="rule-description"></a>Descrizione della regola
 Oggetto [definizione DTD (Document Type Definition)](https://msdn.microsoft.com/library/aa468547.aspx) è uno dei due modi in cui un parser XML può determinare la validità di un documento, come definito per il [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Questa regola cerca le proprietà e le istanze in cui vengono accettati i dati non attendibili per avvisare gli sviluppatori potenziale [divulgazione](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) minacce, con conseguente [Denial of Service (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) attacchi. Questa regola viene attivata quando:

-   <xref:System.Xml.XmlDocument> o <xref:System.Xml.XmlTextReader> classi usano valori resolver predefiniti per l'elaborazione della DTD.

-   Non è definito alcun costruttore per le classi derivate XmlDocument o XmlTextReader oppure non sono usati valori sicuri per <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

-   Rilevare ed elaborare tutte le eccezioni XmlTextReader correttamente per evitare la divulgazione di informazioni di percorso.

-   Usare <xref:System.Xml.XmlSecureResolver>posto di XmlResolver per limitare le risorse a cui può accedere XmlTextReader.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```


