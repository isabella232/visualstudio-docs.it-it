---
title: 'CA3077: elaborazione non sicura in progettazione API, documento XML e lettore di testo XML | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 83132da4b6687db74920015df0ad817eb75673db
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669043"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Elaborazione non sicura in progettazione API, documenti XML e lettori di testo XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Quando si progetta un'API derivata da XMLDocument e XMLTextReader, tenere presente <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Se si usano istanze di DTDProcessing non protette per fare riferimento o risolvere origini di entità esterne oppure per impostare valori non protetti nel codice XML, si può causare la divulgazione di informazioni.

## <a name="rule-description"></a>Descrizione della regola
 La [definizione DTD (Document Type Definition)](https://msdn.microsoft.com/library/aa468547.aspx) rappresenta uno dei due modi in cui un parser XML può determinare la validità di un documento, come definito dalla raccomandazione  [W3C (World Wide Web Consortium) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Questa regola cerca le proprietà e le istanze in cui vengono accettati i dati non attendibili per avvisare gli sviluppatori delle minacce potenziali di [Information Disclosure](https://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) , che possono causare attacchi [Denial of Service (DoS)](https://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) . Questa regola viene attivata quando:

- le classi <xref:System.Xml.XmlDocument> o <xref:System.Xml.XmlTextReader> usano valori di resolver predefiniti per l'elaborazione di DTD.

- Non è definito alcun costruttore per le classi derivate XmlDocument o XmlTextReader oppure non sono usati valori sicuri per <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

- Rilevare ed elaborare correttamente tutte le eccezioni XmlTextReader per evitare la divulgazione di informazioni sul percorso.

- Usare  <xref:System.Xml.XmlSecureResolver>instead di XmlResolver per limitare le risorse a cui XmlTextReader può accedere.

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
