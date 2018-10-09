---
title: 'Procedura: generare modelli da modelli utilizzando le sequenze di Escape | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7cc523aed43dfbe3339c3f3cc054c09b39a4f060
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531029"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Procedura: generare modelli da modelli utilizzando sequenze di escape
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: generare modelli da modelli da utilizzando sequenze di Escape](https://docs.microsoft.com/visualstudio/modeling/how-to-generate-templates-from-templates-by-using-escape-sequences).  
  
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


