---
title: Attività AssignTargetPath | Microsoft Docs
description: Usare l'attività AssignTargetPath di MSBuild per accettare un elenco di file e aggiungere gli attributi TargetPath se non sono già specificati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e56bb8817551e24d1b5aceef2f571e35f1db43e
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353330"
---
# <a name="assigntargetpath-task"></a>Attività AssignTargetPath

Questa attività accetta un elenco di file e aggiunge gli attributi `<TargetPath>`, se non sono già specificati.

## <a name="task-parameters"></a>Parametri dell'attività

Nella tabella che segue vengono descritti i parametri dell'attività `AssignTargetPath` .

|Parametro|Descrizione|
|---------------|-----------------|
|`RootFolder`|Parametro di input `string` facoltativo.<br /><br /> Contiene il percorso della cartella contenente i collegamenti alla destinazione.|
|`Files`|Parametro di input <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco di file in ingresso.|
|`AssignedFiles`|Facoltativo<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`parametro di output.<br /><br /> Contiene l'elenco di file risultante.|

## <a name="remarks"></a>Commenti

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

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

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
