---
title: Attività ZipDirectory | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1092add6386ccc5bc1de78efcf7b623a617d920b
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183067"
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
|`Overwrite`|Parametro `Boolean` facoltativo.<br /><br /> Se `true` , il file di destinazione verrà sovrascritto, se esistente. Il valore predefinito è `false`.|
|`SourceDirectory`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica la directory da cui creare un archivio con estensione *zip*.|

## <a name="remarks"></a>Commenti

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 L'esempio seguente, se usato come file con *estensione targets* importato, crea un archivio *zip* dalla directory di output dopo la compilazione di un progetto. La `$(OutputPath)` proprietà verrebbe normalmente definita in un file di progetto MSBuild, quindi un file di progetto che importa il file seguente produrrebbe un archivio zip `output.zip` :

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
