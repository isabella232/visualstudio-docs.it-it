---
title: Direttiva import T4
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a28bedd01e3a4f6a7a87b025ac9a9a6184da9b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591866"
---
# <a name="t4-import-directive"></a>Direttiva import T4

Nei blocchi di codice di un modello di testo T4 di Visual Studio, la `import` direttiva consente di fare riferimento agli elementi in un altro spazio dei nomi senza fornire un nome completo. È l'equivalente di `using` in C# o di `imports` in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Per una panoramica generale sulla scrittura di modelli di testo T4, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).

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

- Spazio dei nomi del linguaggio DSL

## <a name="see-also"></a>Vedere anche

- [Direttiva assembly T4](../modeling/t4-assembly-directive.md)
