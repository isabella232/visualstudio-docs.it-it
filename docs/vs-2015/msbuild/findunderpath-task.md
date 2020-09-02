---
title: Attività FindUnderPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c679352fb8db81379ab93e800efa9f631773c36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149733"
---
# <a name="findunderpath-task"></a>Attività FindUnderPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Determina gli elementi di una raccolta specificata i cui percorsi sono presenti nella cartella indicata e nelle relative sottocartelle.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `FindUnderPath` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Files`|Parametro facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Specifica i file i cui percorsi devono essere confrontati con il percorso specificato dal parametro `Path`.|  
|`InPath`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi che sono stati trovati nel percorso specificato.|  
|`OutOfPath`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene gli elementi che non sono stati trovati nel percorso specificato.|  
|`Path`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il percorso della cartella da usare come riferimento.|  
|`UpdateToAbsolutePaths`|Parametro `Boolean` facoltativo.<br /><br /> Se true, i percorsi degli elementi di output vengono aggiornati in modo da essere percorsi assoluti.|  
  
## <a name="remarks"></a>Osservazioni  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa l'attività `FindUnderPath` per determinare se i file contenuti nell'elemento `MyFiles` hanno percorsi esistenti nel percorso specificato dalla proprietà `SearchPath`. Al termine dell'attività, l'elemento `FilesNotFoundInPath` contiene il file `File1.txt` e l'elemento `FilesFoundInPath` contiene il file `File2.txt`.  
  
```  
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
 [Riferimento attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
