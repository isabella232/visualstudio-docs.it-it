---
title: 'Procedura: Generare modelli da modelli usando sequenze di escape'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c50fb897e3374eccca60f3fc05591bbf221670e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926034"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Procedura: Generare modelli da modelli usando sequenze di escape
È possibile creare un modello di testo che crea un altro modello di testo come output testo generato. A tale scopo, è necessario utilizzare le sequenze di escape per delineare i tag di modello di testo. Se non si utilizza le sequenze di escape, il modello di testo generato avrà un significato predefinito. Per altre informazioni sull'uso di sequenze di escape in modelli di testo, vedere [usando le sequenze di Escape in modelli di testo](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Per generare un modello di testo all'interno di un modello di testo

-   Usare la barra rovesciata (\\) come carattere di escape per produrre il tag di markup necessari all'interno del modello di testo per le direttive, istruzioni, espressioni e funzionalità in un file di modello di testo separato di classe.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Esempio
 L'esempio seguente Usa caratteri di escape per produrre un modello di testo da un modello di testo. Il `output` direttiva imposta il tipo di file di destinazione per il tipo di file di modello di testo (con estensione TT).

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 L'output di testo generato è un modello di testo.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```