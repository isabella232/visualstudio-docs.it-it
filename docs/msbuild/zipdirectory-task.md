---
title: Attività ZipDirectory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc46e664bd117827be3534c7aa81978d7cc03d5e
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231301"
---
# <a name="zipdirectory-task"></a>Attività ZipDirectory
Crea un archivio con estensione *zip* dal contenuto di una directory.

>[!NOTE]
>L'attività `ZipDirectory` è disponibile solo in MSBuild 15.8 e versioni successive.
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `ZipDirectory` .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`DestinationFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio<br /><br /> Percorso completo del primo file con estensione *zip* da creare.|
|`Overwrite`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, il file di destinazione, se disponibile, verrà sovrascritto. Il valore predefinito è `false`.|
|`SourceDirectory`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica la directory da cui creare un archivio con estensione *zip*.|
  
## <a name="remarks"></a>Note  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [Classe di base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente crea un archivio con estensione *zip* dalla directory di output dopo la compilazione di un progetto.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <ZipOutputPath>$(MSBuildProjectDirectory)</ZipOutputPath>
    </PropertyGroup>

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip">
        />
    </Target>

</Project>
```
  
## <a name="see-also"></a>Vedere anche  
 [Attività](../msbuild/msbuild-tasks.md)   
 [Riferimenti delle attività MSBuild](../msbuild/msbuild-task-reference.md)
