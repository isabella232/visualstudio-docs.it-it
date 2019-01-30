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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f15e11f563a96c9376f7c50b6db7de83abee396e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001709"
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