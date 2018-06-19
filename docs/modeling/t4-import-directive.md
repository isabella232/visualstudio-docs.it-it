---
title: Direttiva import T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4017ffc67558f6056cb01bf62c5adf9e7569ad4d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946910"
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

- [Direttiva assembly T4](../modeling/t4-assembly-directive.md)