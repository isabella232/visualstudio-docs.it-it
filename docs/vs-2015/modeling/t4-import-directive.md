---
title: T4 Direttiva Import | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 00033640ec7810f97785b38437795906500a7866
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163665"
---
# <a name="t4-import-directive"></a>Direttiva import T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nei blocchi di codice di un modello di testo T4 di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], la direttiva `import` consente di fare riferimento agli elementi in un altro spazio dei nomi senza fornire un nome completo. È l'equivalente di `using` in C# o di `imports` in [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
 Per una panoramica generale della scrittura di modelli di testo T4, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).  
  
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
  
- `System`  
  
  Inoltre, se si utilizza una direttiva personalizzata, il processore di direttiva potrebbe importare alcuni spazi dei nomi automaticamente.  
  
  Ad esempio, se si scrivono modelli per un linguaggio DSL, non è necessario scrivere direttive di importazione per gli spazi dei nomi seguenti:  
  
- `Microsoft.VisualStudio.Modeling`  
  
- Lo spazio dei nomi del linguaggio DSL  
  
## <a name="see-also"></a>Vedere anche  
 [Direttiva assembly T4](../modeling/t4-assembly-directive.md)
