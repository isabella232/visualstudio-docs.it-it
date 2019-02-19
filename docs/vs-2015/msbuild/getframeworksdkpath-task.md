---
title: Attività GetFrameworkSdkPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 16a522044188db854b89f87ccba0ef3393ab70fc
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2019
ms.locfileid: "54803936"
---
# <a name="getframeworksdkpath-task"></a>Attività GetFrameworkSdkPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Recupera il percorso di [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkSdkPath`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 2.0, se presente. In caso contrario restituisce `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 3.5, se presente. In caso contrario restituisce `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Parametro di output `String` di sola lettura facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 4.0, se presente. In caso contrario restituisce `String.Empty`.|  
|`Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso della versione più recente di .NET SDK, se sono presenti delle versioni. In caso contrario restituisce `String.Empty`.|  
  
## <a name="remarks"></a>Osservazioni  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività `GetFrameworkSdkPath` per archiviare il percorso a [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] nella proprietà `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
