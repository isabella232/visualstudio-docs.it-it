---
title: Attività Delete | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634279"
---
# <a name="delete-task"></a>Delete (attività)

Elimina i file specificati.

## <a name="parameters"></a>Parametri

Nella tabella che segue vengono descritti i parametri dell'attività `Delete`.

|Parametro|Descrizione|
|---------------|-----------------|
|`DeletedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file che sono stati eliminati correttamente.|
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da eliminare.|
|`TreatErrorsAsWarnings`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, gli errori vengono registrati come avvisi. Il valore predefinito è `false`.|

## <a name="remarks"></a>Note

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Prestare attenzione quando si usano caratteri jolly con l'attività `Delete`. È possibile eliminare facilmente i file non corretti con espressioni come `$(SomeProperty)\**\*.*` o `$(SomeProperty)/**/*.*`, soprattutto se la proprietà restituisce una stringa vuota, nel qual caso il parametro `Files` può restituire la radice dell'unità ed eliminare molto più di quanto si vuole eliminare.

## <a name="example"></a>Esempio

Nell'esempio seguente viene eliminato il file *MyApp.pdb*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
