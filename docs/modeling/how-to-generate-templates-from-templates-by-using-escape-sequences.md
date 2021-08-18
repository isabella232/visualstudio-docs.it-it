---
title: Generare un modello di testo da un modello di testo
description: Vengono fornite informazioni su come generare un modello di testo da un altro modello di testo usando sequenze di escape.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: b406fc50f2527c7e2c6f1f3a553967fe836a1477
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085592"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Procedura: generare modelli da modelli utilizzando sequenze di escape
È possibile creare un modello di testo che crea un altro modello di testo come output di testo generato. A tale scopo, è necessario usare sequenze di escape per delineare i tag del modello di testo. Se non si usano sequenze di escape, il modello di testo generato avrà un significato predefinito. Per altre informazioni sull'uso delle sequenze di escape nei modelli di testo, vedere [Uso delle sequenze di escape nei modelli di testo](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Per generare un modello di testo dall'interno di un modello di testo

- Usare la barra rovesciata ( ) come carattere di escape per produrre i tag di markup necessari all'interno del modello di testo per direttive, istruzioni, espressioni e funzionalità di classe in un file di modello di testo \\ separato.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono utilizzati caratteri di escape per produrre un modello di testo da un modello di testo. La `output` direttiva imposta il tipo di file di destinazione sul tipo di file modello di testo (.tt).

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
