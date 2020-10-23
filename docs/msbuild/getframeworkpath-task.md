---
title: Attività GetFrameworkPath | Microsoft Docs
description: Informazioni su come usare l'attività GetFrameworkPath di MSBuild per recuperare il percorso degli assembly di .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d54a1029805066f5477cb552f5fcf3f2e09598b
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436832"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath (attività)

Recupera il percorso degli assembly di .NET Framework.
Recupera il percorso degli assembly di .NET Framework.

## <a name="task-parameters"></a>Parametri dell'attività

Nella tabella che segue vengono descritti i parametri dell'attività `GetFrameworkPath` .

|Parametro|Descrizione|
|---------------|-----------------|
|`FrameworkVersion11Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 1.1 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion20Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 2.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion30Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion35Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 3.5 del framework, se presenti. In caso contrario restituisce `null`.|
|`FrameworkVersion40Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly della versione 4.0 del framework, se presenti. In caso contrario restituisce `null`.|
|`Path`|Parametro di ouput facoltativo `String`.<br /><br /> Contiene il percorso agli assembly del framework più recente, se disponibili. In caso contrario restituisce `null`.|

## <a name="remarks"></a>Commenti

Se sono installate diverse versioni del .NET Framework, questa attività restituisce la versione progettata per l'esecuzione di MSBuild.

Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension> , che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task> . Per un elenco di questi parametri aggiuntivi e le relative descrizioni, vedere [classe di base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Esempio

Nell'esempio seguente viene usata l'attività `GetFrameworkPath` per archiviare il percorso a .NET Framework nella proprietà `FrameworkPath`.

```xml
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

- [Attività](../msbuild/msbuild-tasks.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
