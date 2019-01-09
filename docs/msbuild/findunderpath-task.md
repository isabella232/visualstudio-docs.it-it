---
title: Attività FindUnderPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 865e291e24bfb161f43e8fb5192a08e93cdb75d0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869099"
---
# <a name="findunderpath-task"></a>FindUnderPath (attività)
Determina gli elementi di una raccolta specificata i cui percorsi sono presenti nella cartella indicata e nelle relative sottocartelle.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `FindUnderPath` .  
  
|Parametro|Description|  
|---------------|-----------------|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file i cui percorsi devono essere confrontati con il percorso specificato dal parametro `Path`.|  
|`InPath`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi che sono stati trovati nel percorso specificato.|  
|`OutOfPath`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi che non sono stati trovati nel percorso specificato.|  
|`Path`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il percorso della cartella da usare come riferimento.|  
|`UpdateToAbsolutePaths`|Parametro `Boolean` facoltativo.<br /><br /> Se true, i percorsi degli elementi di output vengono aggiornati in modo da essere percorsi assoluti.|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'attività `FindUnderPath` per determinare se i file contenuti nell'elemento `MyFiles` hanno percorsi esistenti nel percorso specificato dalla proprietà `SearchPath`. Al termine dell'attività, l'elemento `FilesNotFoundInPath` contiene il file *File1.txt* e l'elemento `FilesFoundInPath` contiene il file *File2.txt*.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività MSBuild](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)