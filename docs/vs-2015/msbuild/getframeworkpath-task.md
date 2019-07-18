---
title: Attività GetFrameworkPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b528d0a4971d1d070c69d12cdb9a693d9a30f20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149491"
---
# <a name="getframeworkpath-task"></a>Attività GetFrameworkPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Recupera il percorso degli assembly [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkPath`.  
  
|Parametro|DESCRIZIONE|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 1.1 del framework, se presenti. In caso contrario restituisce `null`.|  
|`FrameworkVersion20Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 2.0 del framework, se presenti. In caso contrario restituisce `null`.|  
|`FrameworkVersion30Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.0 del framework, se presenti. In caso contrario restituisce `null`.|  
|`FrameworkVersion35Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.5 del framework, se presenti. In caso contrario restituisce `null`.|  
|`FrameworkVersion40Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 4.0 del framework, se presenti. In caso contrario restituisce `null`.|  
|`Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly del framework più recente, se disponibili. In caso contrario restituisce `null`.|  
  
## <a name="remarks"></a>Osservazioni  
 Se sono installate diverse versioni di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], l'attività restituisce la versione in cui deve essere eseguito [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] in base alla progettazione.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usata l'attività `GetFrameworkPath` per archiviare il percorso a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] nella proprietà `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
