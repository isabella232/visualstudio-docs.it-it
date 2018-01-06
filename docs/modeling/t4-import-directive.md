---
title: T4 Direttiva Import | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 5d581e182b39ac5a786b2d66a1a3798ba7fe82ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="t4-import-directive"></a>Direttiva import T4
Nei blocchi di codice di un modello di testo T4 di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la direttiva `import` consente di fare riferimento agli elementi in un altro spazio dei nomi senza fornire un nome completo. È l'equivalente di `using` in C# o di `imports` in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Per una panoramica generale di scrittura di modelli di testo T4, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>Utilizzo della direttiva Import  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 In questo esempio, il codice del modello può omettere uno spazio dei nomi esplicito per i membri di System.IO:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## <a name="standard-imports"></a>Importazioni standard  
 Lo spazio dei nomi seguente viene importato automaticamente, in modo che non sia necessario scrivere una direttiva di importazione:  
  
-   `System`  
  
 Inoltre, se si utilizza una direttiva personalizzata, il processore di direttiva potrebbe importare alcuni spazi dei nomi automaticamente.  
  
 Ad esempio, se si scrivono modelli per un linguaggio DSL, non è necessario scrivere direttive di importazione per gli spazi dei nomi seguenti:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Spazio dei nomi del linguaggio DSL  
  
## <a name="see-also"></a>Vedere anche  
 [Direttiva assembly T4](../modeling/t4-assembly-directive.md)