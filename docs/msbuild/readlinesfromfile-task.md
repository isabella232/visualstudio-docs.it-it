---
title: Attività ReadLinesFromFile | Microsoft Docs
description: Informazioni su come MSBuild usa l'attività ReadLinesFromFile per leggere un elenco di elementi da un file di testo. Il file deve contenere un elemento in ogni riga.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff2c43af40ea429714f0624db67c53fa46eb6427
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048774"
---
# <a name="readlinesfromfile-task"></a>ReadLinesFromFile (attività)

Legge un elenco di elementi da un file di testo.

## <a name="parameters"></a>Parametri

 Nella tabella che segue vengono descritti i parametri dell'attività `ReadLinesFromFile` .

|Parametro|Descrizione|
|---------------|-----------------|
|`File`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file da leggere. Il file deve contenere un elemento in ogni riga.|
|`Lines`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene le righe lette dal file.|

## <a name="remarks"></a>Commenti

 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

 L'esempio seguente usa l'attività `ReadLinesFromFile` per creare gli elementi da un elenco in un file di testo. Gli elementi letti dal file vengono archiviati nella raccolta di elementi `ItemsFromFile`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [Attività](../msbuild/msbuild-tasks.md)
