---
title: Usare sequenze di escape per generare modelli da modelli
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a9afe2670bb086627407a9f1bc674edfc2fe354
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72605461"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Procedura: generare modelli da modelli utilizzando sequenze di escape
È possibile creare un modello di testo che crea un altro modello di testo come output di testo generato. A tale scopo, è necessario utilizzare sequenze di escape per delineare i tag del modello di testo. Se non si utilizzano sequenze di escape, il modello di testo generato avrà un significato predefinito. Per ulteriori informazioni sull'utilizzo di sequenze di escape nei modelli di testo, vedere [utilizzo di sequenze di escape in modelli di testo](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Per generare un modello di testo dall'interno di un modello di testo

- Utilizzare la barra rovesciata (\\) come carattere di escape per produrre i tag di markup necessari all'interno del modello di testo per le direttive, le istruzioni, le espressioni e le funzionalità di classe in un file di modello di testo separato.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono utilizzati caratteri di escape per produrre un modello di testo da un modello di testo. La direttiva `output` imposta il tipo di file di destinazione sul tipo di file del modello di testo (con estensione TT).

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