---
title: Attività ZipDirectory | Microsoft Docs
description: Informazioni su MSBuild usa l'attività ZipDirectory per creare un .zip archivio dal contenuto di una directory.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0110224fb885d6fdb125e187b4233f1a34a9b11d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039865"
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

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e delle relative descrizioni, vedere [Classe di base TaskExtension.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Esempio

 L'esempio seguente (se usato come file con  estensione *targets* importato) crea un archivio.zipdalla directory di output dopo la compilazione di un progetto. La proprietà verrebbe in genere definita in un file MSBuild di progetto, quindi un file di progetto che importa il file seguente produrrebbe `$(OutputPath)` un archivio `output.zip` ZIP:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
