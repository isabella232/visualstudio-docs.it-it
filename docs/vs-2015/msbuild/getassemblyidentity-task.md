---
title: Attività GetAssemblyIdentity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b4a578d1d22c6e912fd3f7edc203195dbba8987
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666078"
---
# <a name="getassemblyidentity-task"></a>Attività GetAssemblyIdentity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Recupera le identità degli assembly dai file specificati ed estrae le informazioni sulle identità.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
 Nella tabella che segue vengono descritti i parametri dell'attività `GetAssemblyIdentity`.  
  
|Parametro|Description|  
|---------------|-----------------|  
|`Assemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene le identità di assembly recuperate.|  
|`AssemblyFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da cui recuperare le identità.|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi estratti dal parametro `Assemblies` contengono voci di metadati degli elementi denominati `Version`, `PublicKeyToken` e `Culture`.  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente l'identità dei file specificati nell'elemento `MyAssemblies` viene recuperata ed estratta nell'elemento `MyAssemblyIdentities`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
