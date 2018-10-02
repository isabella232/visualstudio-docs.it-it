---
title: Attività AssignCulture | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ee44937f48101454a00128405fb03ce4260de4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518991"
---
# <a name="assignculture-task"></a>Attività AssignCulture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [attività AssignCulture](https://docs.microsoft.com/visualstudio/msbuild/assignculture-task).  
  
  
Questa attività accetta un elenco di elementi che possono contenere una stringa dell'identificatore di impostazioni cultura .NET valida come parte del nome file e genera elementi con metadati denominati `Culture` che contengono l'identificatore di impostazioni cultura corrispondente. Ad esempio, il nome di file Form1.fr-fr.resx contiene un identificatore di impostazioni cultura incorporato, "fr-fr", quindi questa attività genera un elemento con lo stesso nome di file con i metadati `Culture` uguali a `fr-fr`. L'attività genera inoltre un elenco di nomi di file con le impostazioni cultura rimosse dal nome del file.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `AssignCulture`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssignedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco di elementi ricevuti nel parametro `Files`, con una voce di metadati `Culture` aggiunta a ogni elemento.<br /><br /> Se l'elemento proveniente dal parametro `Files` contiene già una voce di metadati `Culture`, viene usata la voce di metadati originale.<br /><br /> L'attività assegna una voce di metadati `Culture` solo se il nome del file contiene un identificatore di impostazioni cultura valido. L'identificatore di impostazioni cultura deve essere compreso tra gli ultimi due punti nel nome file.|  
|`AssignedFilesWithCulture`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene il subset degli elementi del parametro `AssignedFiles` che hanno una voce di metadati `Culture`.|  
|`AssignedFilesWithNoCulture`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene il subset degli elementi del parametro `AssignedFiles` che non hanno una voce di metadati `Culture`.|  
|`CultureNeutralAssignedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene lo stesso elenco di elementi generato nel parametro `AssignedFiles`, eccetto le impostazioni cultura rimosse dal nome del file.<br /><br /> L'attività rimuove le impostazioni cultura dal nome del file solo se viene usato un identificatore di impostazioni cultura valido.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica l'elenco di file con nomi di impostazioni cultura incorporati a cui assegnare le impostazioni cultura.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene eseguita l'attività `AssignCulture` con la raccolta di elementi `ResourceFiles`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <ResourceFiles Include="MyResource1.fr.resx"/>  
        <ResourceFiles Include="MyResource2.XX.resx"/>  
    </ItemGroup>  
  
    <Target Name="Culture">  
        <AssignCulture  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
            <Output TaskParameter="AssignedFilesWithCulture"  
                ItemName="OutAssignedFilesWithCulture"/>  
            <Output TaskParameter="AssignedFilesWithNoCulture"  
                ItemName="OutAssignedFilesWithNoCulture"/>  
            <Output TaskParameter="CultureNeutralAssignedFiles"  
                ItemName="OutCultureNeutralAssignedFiles"/>  
        </AssignCulture>  
    </Target>  
</Project>  
```  
  
 La tabella seguente descrive il valore degli elementi di output dopo l'esecuzione dell'attività. I metadati degli elementi vengono visualizzati tra parentesi dopo l'elemento.  
  
|Raccolta di elementi|Sommario|  
|---------------------|--------------|  
|`OutAssignedFiles`|`MyResource1.fr.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx` (senza metadati aggiuntivi)|  
|`OutAssignedFilesWithCulture`|`MyResource1.fr.resx (Culture="fr")`|  
|`OutAssignedFilesWithNoCulture`|`MyResource2.XX.resx` (senza metadati aggiuntivi)|  
|`OutCultureNeutralAssignedFiles`|`MyResource1.resx (Culture="fr")`<br /><br /> `MyResource2.XX.resx (` (senza metadati aggiuntivi)|  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)



