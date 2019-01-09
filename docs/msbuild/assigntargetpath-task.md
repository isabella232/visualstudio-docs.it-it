---
title: Attività AssignTargetPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a711c20198b117b53536f9b0fe043a468eb8a0b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930661"
---
# <a name="assigntargetpath-task"></a>Attività AssignTargetPath
Questa attività accetta un elenco di file e aggiunge gli attributi `<TargetPath>`, se non sono già specificati.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `AssignTargetPath` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`RootFolder`|Parametro di input `string` facoltativo.<br /><br /> Contiene il percorso della cartella contenente i collegamenti alla destinazione.|  
|`Files`|Parametro di input <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco di file in ingresso.|  
|`AssignedFiles`|Facoltativo<br /><br /> Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Contiene l'elenco di file risultante.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene eseguita l'attività `AssignTargetPath` per configurare un progetto.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)